---
title: "Headphones not working on Hardy laptop"
date: 2008-05-01
forum: Hardware
---

### Post by Apreche on 2008-05-01
I have a Fujitsu P7230 laptop. In gutsy all the audio worked just fine. In Hardy, it mostly works. However, there are problems with the headphones.

If I play audio, it comes out of the built-in speakers just fine. If I connect headphones, the speakers turn off, as they should. However, no audio comes out of the headphones. There is no headphone volume in the mixer, but there is an option for "headphone as line-out". Enabling this option works. It sends completely non-amplified line-out audio from the headphone hole. It's nice that this feature works, as it can sometimes be useful when using an external amplifier, but not when using headphones to watch movies during my commute on the train.

I tried [this fix]("https://answers.launchpad.net/ubuntu/+question/28387"), and it helped a little. Now the correct output comes to the headphone, but the built-in speakers don't work at all!

Here is my lspci

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

I've seen a lot of other threads discussing similar issues, but none of them seemed to exactly match my situation.

---

