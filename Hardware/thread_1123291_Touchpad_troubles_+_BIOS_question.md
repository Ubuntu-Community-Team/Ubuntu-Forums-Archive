---
title: "Touchpad troubles + BIOS question"
date: 2009-04-12
forum: Hardware
---

### Post by drummerchrissk on 2009-04-12
So, I've been dealing with a broken touchpad for quite a few months now. I'm using a Compaq Armada E500. I have searched for Ubuntu drivers for it to no avail. I did a google search for touchpad drivers in Ubuntu and my number 1 result was [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) where it said 

> Ubuntu provides configuration of the most common touchpad options in System > Preferences > Mouse, under the Touchpad tab.

Now this might be a great starting point if I had a touchpad tab where they said I should have one. I cannot find anything about getting this to work.

Someone I know personally told me to get into my BIOS and see if the touchpad had been disabled. Here's my second issue. I boot my computer, and when it says F12 = Network Service Boot, I hit the F12 key. Nothing happens. I hit it multiple times and then it starts making a beep noise every time I hit it. My question is if this isn't the way into the BIOS, then what is? Secondly, I know that, depending on different computers, the key that grants you access to the BIOS can be different. I was wondering if that key is determined by something in the motherboard or in the hardrive.

I am, for the most part, fairly new to the computer scene on a technical level so sorry if these aren't exactly intelligent questions.

Anyways if you know of an available driver for a touchpad then please let me know.

Happy Easter!

---

### Post by itkeepsrepeating on 2009-04-13
That's an interesting laptop. Here's a link for the manual:
[http://www.bio.ifi.lmu.de/~steiner/linux/128679-004.pdf](http://www.bio.ifi.lmu.de/~steiner/linux/128679-004.pdf)

I think you hit f10 when the blinking cursor shows in the upper right corner of the screen. That should get you into BIOS. 

It stands to reason that if you don't have a touchpad tab, the computer doesn't think you have a touchpad. BIOS could well be the culprit, and you should check that first.

---

### Post by drummerchrissk on 2009-04-14
So F10 worked and got me into the BIOS. Thank you!

Also I'm sure that the manual you sent will help me configure my touchpad once again. In the BIOS I took a look under device options and under 'Multiple Pointing Devices' Disabled was selected so I changed that in hopes that it's the answer. If not, I at least have a good start on it.

So thanks again for the quick reply, the maunal and your fix for my BIOS troubles.

---

### Post by itkeepsrepeating on 2009-04-14
No problem. I'm just glad to give back to the Ubuntu community what I can, as they've held my hand through several daunting tasks over the past couple years. 

New to computers? You can save yourself from asking many questions in less forgiving forums by searching google.com for your problem. If you're using Firefox as your web browser, the upper-right corner has a box that searches from wherever you are. Try googling "how to ______" for almost anything, computer-related or not. "How to use google" is a great starting point, as it will help you to better find what you want to know.

---

### Post by drummerchrissk on 2009-04-14
I agree with you. Ubuntu itself as well as the community it holds have so much to offer. I've never seen a community as tight knit as the Ubuntu community.

I'm new to computers on a more technical level. I've been busy reading books on and off the internet, learning as much as I can and just recently began learning about the kernal itself. So I'm hoping that this summer will be a great learning experience for me.

---

