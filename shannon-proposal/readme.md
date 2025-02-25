# Sentry docs review

## Description
This is Shannon's assessment of Sentry's docs in general, and specifically, the [tracing](https://docs.sentry.io/platforms/javascript/guides/nextjs/tracing/) docs in Sentry's next.js platform.

## Table of Contents
- [Tracing feedback](#tracing)
- [General docs feedback](#General-docs-feedback)
- [Contact](#contact)

## Tracing

I focused on the next.js tracing article.

[Updates](https://github.com/sfanahata/sentry-docs/blob/v1-updates/docs/platforms/javascript/common/tracing/index.mdx) can be found in the `v1-updates` branch, but review the readme first.

### Overview
Tracing documentation got me what I needed, but took too long to understand how to get it done. 

- How and when to use the options for testing vs usage was unclear. This could lead to failed testing or a need to troublesoot.
<br>
- Why to drop my `tracesSampleRate` was unclear, which can lead to mistrust, since not doing so can lead to higher billing.
<br>
- Order of exposition meant I couldn't easily scan the doc to do a quick configuration.
<br>
- It was hard to tell, after looking at the code, how the docs site was assessing what conditions to use to present me information, which could lead to some developers missing key details about the product.

#### Personas

The developer audience is baseline technically proficient. If they're coming to learn about Sentry SDKs, chances are they already have familiarity with the platform they're researching. That said, Sentry documentation seems to be targeted at hands-on developers. 

While the overview section of each article can be a helpful starting point if reading the entire article, an engineering leader might have a harder time seeing the comprehesive feature set Sentry has to offer. Linking more directly to the product walkthroughs in each platform, or even having an introductory article could help these folks feel more in the know. 

That said, Sentry comes across as more of a bottoms up adoption type product right now, and I would prioritize making sure that hands-on-keys developers are the main focus for our documentation. 

### Structure and content

I keyed in on two themes for improving the tracing doc: 

1. Get straight to configuration. We already set up an exposition of what tracing is about, and link out to some useful documentation for details. I set up a quick start section directly below, combining information that was spread out across the doc into 2.5 steps to set up sample rates.
<br>
2. Clarifying wording and meaning. I shortened sentences where possible, and I clarified what we meant by certain callouts. For example, I directly mention *why* it is important to drop the `tracesSampleRate` option down from `1.0`. 

I also noticed that Sentry was showcasing this link to profiling. It comes across as a rabbit hole positioned so high up the page, without much context, or direct demonstration of stack traces or flame graphs in the product when I click through to the article. I didn't make changes, but wonder about how Sentry positions related features that we think are valuable to know about.
```sh
<PlatformLink to="/profiling">Set up Profiling</PlatformLink> to get even more detailed tracing information like stack traces and flame graphs.
```

### Challenges and trade-offs 

The way I organize the tracing article does pose a couple of challenges and trade-offs: 

- Being a little repetative. Repetition does not kill the prayer, but it can make documentation redundant. I worked to minimize redundancy, but still circled back after the quick start to explain both options, as well as both types of instrumetation. This might lead some to wonder where more detail is, however the article is so short, they'll find the answer quickly. We could link to further down the page, or be clever in other ways, if we found that people were not finding the information through feedback, user testing, and/or instrumentation to see how people were interracting with the page.
<br>
- Making sure this shortened artcile configuration works for all possible platform set-ups. I could not quite verify whether or not it worked for all scenarios. 
<br>
- Breaking formatting across all docs. This is potentially a new way to format articles. Do we want it to be uniform? That could take a lot of work to prioritize across all docs. 

## General docs feedback

Top pieces of feedback:

- I couldn't tell whether the live documentation was giving me specific information by reading my setup with Sentry, or assuming I was not set up at all with Sentry. I couldn't see anywhere where I was logged in on the docs site, but reading through the code, it's clear that there are conditions that make the docs read different ways. **Suggestion**: Make it clear whether or not I'm connected to my Sentry account while browsing, and what platform I'm being filtered through. 
<br>
- Navigation was sometimes hard. For example, I got lost when I was bounced from next.js platform docs to product walkthroughs for tracing. **Suggestion**: Have a pop-up modal that previews or embeds a smaller window of the linked-to article in the primary article when hovering on or clicking a linked-to article. This might be pie in the sky, but would make reviewing doc way more fun!
<br>
- I stumbled upon a docs area that shared the overarching philosophy of Sentry’s SDKs. I thought it was related to the docs contribution section, but it wasn’t. I have no idea how I got there, and I couldn't find it again without googling. Lo and behold, it wasn't just one page, but an entire section! Why is there a docs.sentry.io and a develop.sentry.dev/getting-started/, and they’re not connected at all? **Suggestion**: Bring in develop.sentry.dev, or have a link to it somwhere like we link to the repo. 

### Docs validation

Here are some ways that I would validate the value and usability of our docs. We probably don't need all these methods, but I would use most of them if available.

- Perform regular reviews of all of the issues, running them through a filter that looked for similar issues to address at once. 
<br>
- Do internal testing with developers at Sentry to ask them to review the docs and complete the tasks. Or maybe better yet, use the docs as one of the QA testing criteria. Have them narrate their experience and provide feedback with being able to accomplish the tasks. 
<br>
- Check on the yes/no helpful responses already on the site. 
<br>
- Instrument pages, maybe using a 3rd party tool (or Sentry replay?), that allows to watch back user interaction with a page. 
<br>
- Use Pendo, Mixpanel, or our database + instrumentation to understand site visits, and to build funnels to see how far people get on docs, and how much time they spend on each page. Is there a way to see if they have Sentry open at the same time, or start using Sentry right away? 

## Contact
**Me!** Shannon Anahata
**Email** shannon.anahata@gmail.com
