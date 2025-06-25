+++
title = "How I won a startup competition in 3 weeks (and what actually mattered)"
date = 2025-06-25

[taxonomies]
categories = ["Business", "Thoughts", "Guides"]
+++

Three weeks. One idea. Extreme hyperfixation. And somehow, I ended up pitching to investors in Riga after winning a startup competition I barely had time to prepare for. Here's what actually made the difference when everything seemed stacked against me.

<!-- more -->

---

## The Setup: Already Behind

Let me paint the picture first. We're in the final course of Business Academy called "BIP: Technology Startup" - four weeks to build a startup with a chance to make it to the top 5 teams and pitch to real investors in Riga. Sounds exciting, right?

Well, I managed to waste the entire first week. While other teams were already deep into ideation and team formation, I spent the weekend of week one finally coming up with my idea. Classic me - starting with a time disadvantage that would haunt me for the next three weeks.

Oh, and while everyone else had teammates to split the workload, I was flying solo. But honestly? That part didn't bother me much. I'd been building and shipping startups alone for a while now, so at least I was in familiar territory.

The idea that finally clicked was **Soundpack** - a platform to solve the monopolized, limited sound library problem that I faced as a music producer. The existing libraries just weren't cutting it for the variety an average producer actually needs.

## What Everyone Gets Wrong About Startup Success

Here's the thing about startup advice - it's everywhere, and most of it misses the point completely. Everyone talks about having the perfect pitch deck, the most elegant technical solution, or the prettiest UI. The jury that judged our competition? They didn't care about any of that stuff.

What they cared about was something much simpler, yet much harder to achieve: **clarity**.

Out of all the teams, they mentioned that Soundpack had "the clearest use case." Not the most innovative tech stack. Not the most polished presentation. The clearest problem-solution fit.

That distinction changed everything for me, and it should change how you think about building startups too.

## Lesson #1: Solve Your Own Problems (Seriously, This Time)

I know, I know. "Solve your own problems" is startup advice so common it's basically a meme at this point. But here's why it actually worked for me, and why most people still get it wrong:

**It's not about having a problem. It's about having a problem you TRULY care about.**

I sat down and kept asking myself "who am I?" until I couldn't answer anymore. That sounds dramatic, but it forced me to dig into what genuinely frustrated me as a music producer. The sound library situation wasn't just an inconvenience - it was actively holding back my creative process.

When you solve your own problem, three magical things happen:

1. **You understand the pain intimately** - No market research needed when you live the problem daily
2. **You stay motivated during the hard parts** - When you're coding at 2 AM, personal investment beats external motivation every time  
3. **You can spot fake solutions immediately** - You know when something actually solves the problem vs. just looking good on paper

The difference between solving "a problem someone might have" and solving "YOUR problem" is the difference between building a feature and building a business.

## Lesson #2: Focus Beats Everything

This one saved my ass during the competition. While other teams were building comprehensive platforms with multiple features, I focused obsessively on one thing: **making sound discovery actually work**.

Here's the technical insight that mattered: Instead of trying to compete on library size (impossible against established players), I competed on **generation efficiency**. There was no search algorithm - I completely bypassed the discovery problem by having AI generate exactly what producers wanted on demand.

The approach was radical: instead of searching through thousands of existing samples, users describe what they want and the AI creates it from scratch. No more "close enough" - just samples tailored to your exact creative vision. Of course, the fact that the samples are AI genereted wasn't hidden, it just makes the user understand Soundpack's behavior much easier.

The jury noticed this focus immediately. When you solve a single problem for a single market really well, it becomes obvious to everyone what you're doing and why it matters.

## Lesson #3: One Passionate Customer > 1000 Waitlist Signups

This lesson hit me during the actual competition. After my initial pitch to fellow students, several came up to me saying they'd tried Soundpack and loved it. More importantly - they said they'd keep using it.

That feedback was worth more than any analytics dashboard or conversion metric. Why?

**Passionate early users tell you what's actually working.** They don't just download your app - they change their workflow to include it. They tell their friends about it. They give you feedback that actually helps you build the right thing.

Contrast this with the teams that spent time building landing pages and collecting email signups for products that didn't exist yet. Those waitlist numbers look impressive in a pitch deck, but they don't tell you if you're solving a real problem.

## The Technical Reality: Vibecode Everything

Since I had limited time, the technical approach had to be ruthlessly pragmatic. My strategy? **Vibecode the entire app.** No traditional coding, just AI-powered development tools.

### The Vibecode Journey
I started with [Lovable](https://lovable.dev/), but quickly ran into errors and limitations - especially around AI integrations. That's when I switched to [v0 by Vercel](https://v0.dev/), which got everything right pretty damn fast, including the AI integrations for generating initial samples.

### Architecture That Actually Happened
```
Frontend: Next.js (generated by v0)
Backend: Next.js serverless functions 
Database: Supabase
Auth: Supabase Auth
Storage: Supabase Storage
Hosting: Vercel
AI Models: Replicate (stable-audio-open-1.0)
```

The key insight: **Use the stack you know best, even when using AI tools.** I chose Next.js because I'd mastered it, not because it was trendy. Learning new tech mid-sprint is a recipe for disaster.

### The Real MVP Strategy
Instead of traditional search, I built something much cooler - **AI-generated sample packs**:

1. **Parameter Input** - BPM, key, vibe, one-shots vs loops, and most importantly, user prompt
2. **Smart Sample Generation** - Complete sample pack creation and playback 
3. **Download Options** - Individual samples or full zip archives

### The Two-Layer AI System
Here's where it gets interesting. The "search" isn't search at all - it's AI generation with two layers:

**Layer 1: Description Generation**
- ChatGPT o1 takes user parameters (BPM, key, vibe, prompt)
- Generates detailed descriptions for each sample
- Determines optimal sample pack size
- Outputs precise specifications for the audio model

**Layer 2: Audio Generation**  
- [stable-audio-open-1.0](https://replicate.com/stability-ai/stable-audio-open) generates the actual sounds
- Fed the o1-generated descriptions
- Tweaked parameters for short-to-mid length audio optimized for music production
- Hosted on [Replicate](https://replicate.com/) for easy MVP testing

### What Actually Worked (And What Didn't)

**The Wins:**
- [Supabase](https://supabase.com/) handled auth, database, and file storage seamlessly with their convenient SDK
- Audio streaming through Supabase's built-in streaming features
- Using Replicate instead of self-hosting the audio model - perfect for MVP validation
- [Tailwind CSS](https://tailwindcss.com/docs/animation) + shadcn/ui made it look professional with smooth animations

**The Pain Points:**
- **Model cold starts** - Replicate models sometimes went cold, causing 1+ minute wait times for unlucky users
- **Finding the right audio model** - Tried Facebook's models, hobby projects, everything sucked until stable-audio-open
- **UX corners cut** - Long loading times, no mobile optimization, no sample regeneration options

### Performance Where It Actually Mattered
The biggest technical challenge wasn't code optimization - it was **getting the AI to generate good sounds**. I spent most of my time tweaking model parameters until I realized stable-audio-open was the one. The difference between a decent sample and garbage often came down to tiny parameter adjustments.

Users don't care about your elegant backend architecture. They care that the AI actually generates sounds they want to use in their tracks.

## The Final 24 Hours: When Everything Clicked

The real breakthrough happened in the last 24 hours before the Riga trip. I'd made it to the top 5 teams, but now I had to create a pitch deck and prepare for real investors.

I stayed up until 2 AM the night before, finished the deck in Lido (a shopping mall, for context), and somehow it all came together. That final push taught me something crucial about startup building:

**Constraints force clarity.** 

When you have unlimited time, you overthink everything. When you have 24 hours to prepare for the most important pitch of your project, you focus on what actually matters: the problem, the solution, and why people should care.

## What This Actually Means for Solo Founders

Building Soundpack solo taught me that being a one-person team isn't a disadvantage - it's a different game entirely. Here's what actually matters:

### Decision Speed Wins
When you're solo, you can pivot instantly. No stakeholder meetings, no consensus building. I probably made 50+ micro-pivots during those three weeks that a team would have spent days debating.

### Personal Investment Shows
Investors and judges can tell when you're personally invested in solving the problem. It comes through in how you talk about user pain points, how you prioritize features, and how you handle criticism.

### Technical Debt Is Different
In a team, technical debt is dangerous because knowledge gets distributed. Solo, technical debt is just a trade-off you manage consciously. I shipped fast and refactored later, because I knew exactly what corners I'd cut.

## The Unexpected Outcome

Winning the competition wasn't the real victory. The real victory was proving to myself that I could build something people actually wanted, under pressure, completely solo.

But here's the twist - success created its own problems. Suddenly I had to "rearrange my plans for the summer" and figure out what to do with a product that people actually liked.

That's a good problem to have, but it's still a problem. Success in startup competitions is just the beginning, not the end goal.

## What I'd Do Differently

Looking back, here are the things I'd change if I did this again:

1. **Start with the problem, not the solution** - I got lucky that my solution worked, but I should have validated the problem more systematically
2. **Document the journey better** - The technical decisions and user feedback from those three weeks were goldmines I didn't capture properly
3. **Plan for success** - I had no idea what to do if the thing actually worked, which created unnecessary stress post-competition

## The Real Takeaways

If you're building a startup solo, here's what actually matters:

1. **Solve problems you genuinely care about** - Your personal investment will carry you through the inevitable hard parts
2. **Focus ruthlessly on one thing** - Better to be excellent at solving one problem than mediocre at solving ten
3. **Value passionate users over vanity metrics** - One person who changes their workflow for your product is worth 100 email signups
4. **Move fast, but move intelligently** - Speed matters, but not at the expense of understanding your users
5. **Embrace being solo** - It's a feature, not a bug, if you leverage it correctly

## What's Next?

The competition is over, but the real work is just beginning. I'm spending more time figuring out how to turn a three-week sprint into a sustainable business.

The question "What now?" still follows me around, but that's exactly where I want to be - in the uncomfortable place where real growth happens.

And who knows? Maybe the next blog post will be about how I completely screwed up the post-competition phase. That would be pretty on-brand for me.

---

*If you're working on your own startup and want to compare notes on the solo founder experience, or if you're a music producer who wants to try Soundpack, you can find me at [soundpack.app](https://soundpack.app) or just yell at me on whatever social media platform hasn't banned me yet.* 