---
title: "Inspiron 640m headphone jack question"
date: 2009-07-23
forum: Hardware
---

### Post by Crimsonial on 2009-07-23
Alright, I've looked around for about a week now with no luck. Which figures, because it's a relatively unique issue.

Shortly after making the best decision of the past year or so and switching to Ubuntu from Vista on my Inspiron 640m, I broke the plastic seal, if you'd call it that, that keeps the headphone jack in line, basically leaving a completely un-securable plugin. Which can actually be pretty neat, if you fiddle with the cable in just the right way, you can just cut out the voice in music. Anyways, the jack that's typically used for the microphone is in perfect condition.

I know that the hardware is technically capable of switching the audio output to that jack, because I've done it before with a speaker setup in Vista. But that was Vista, and I'm now on unfamiliar grounds.

Is the solution to this right under my nose, or is there some method that someone could give me to get me going in the right direction?

---

### Post by nixscripter on 2009-07-29
Depending on how the card is being driven, you can look into **alsamixer**. It's a command line command which opens a visual mixer in your Termeinal.

There is often a "headphone volume" (which can be adjusted with up and down arrows) or "headphone jack switch" (which can be toggled with M for mute) independent of the other levels. This controls the jack.

You can get more information on the keyboard commands by running **man alsamixer**.

---

