---
title: "What steps can I take to troubleshoot a kernel panic?"
date: 2008-12-17
forum: Hardware
---

### Post by Nixie Pixel on 2008-12-17
The situation:  Over the course of a number of days, my Ubuntu 8.10 laptop crashes about twice a day, freezing, with the Caps Lock key blinking on and off.

Full details about my problem (and the many others with the same problem) [may be found here]("http://ubuntuforums.org/showthread.php?t=976287"), but my question is simple:

What exact steps should I take to get the most information I can about why my system is crashing, in any situation?  I am more concerned about learning how to troubleshoot this problem in Linux than I am solving it (at the moment, at least!).

Thank you!

~Nix

---

### Post by Nixie Pixel on 2008-12-19
I find it hard to believe that no one knows how to troubleshoot a kernel panic.

Is this an area where we can start saying that Windows is superior than Linux?  Or just Windows support better than Ubuntu support?

---

### Post by Captain_tux on 2008-12-20
*Or perhaps a combination of both...?*

Regardless, I believe you can begin some troubleshooting by taking a look at the **/var/log/messages** & **/var/log/syslog** log files. That's not to say that I know what to do once you find something in those files, but at least it's a place to begin.

Buena suerte!

---

### Post by shad0w_walker on 2008-12-20
I have experienced only one issue which caused a kernel panic for me. I had a bar of RAM in my system which developed a fault and when the kernel loaded partly into that RAM, it would become unable to read itself and cause a panic. I'd suggest you run a memtest and see if you are getting any RAM errors.

---

### Post by Captain_tux on 2008-12-20
Just read your blog (and wow... you're a cutie!). 

Anyhow, I had a similar problem to your kernel panics whilst using **Mandriva 2009**. Here's the link to my thread there: [http://forum.mandriva.com/viewtopic.php?t=100256&start=0&postdays=0&postorder=asc&highlight=](http://forum.mandriva.com/viewtopic.php?t=100256&start=0&postdays=0&postorder=asc&highlight=).

Like you, I've yet to find a solution for that freaking problem...

---

### Post by iponeverything on 2008-12-20
I would start ruling things out. 

Two likely culprits:

Video 
Wireless

To rule these out I would:

Try the vesa driver.

If the crash still occurs, pick up a cheap 802.11g usb dongle (zd1211 ones work well) to use for a while and blacklist the driver that you are currently using.

If the crashes still happen I start looking at some of the other modules that you have loaded.  If nothing jumps, out at you. Start digging through launchpad with searches like:

- your MotherBoard model 
- anything that seem unique.

The key is solving the problem is finding a pattern. Is there an application that is always open when the crash happens? Try booting with previous kernel version. What file system are you using?  

- add the applet to panel to monitor temps on your hardware.

There are a number things in the BIOS that also play a part, staring going through every thing in bios and try punching them into launchpad or google with a few other key words.

It does involve quite a bit of detective work, but with a lot of patience and some luck you can get to bottom of it.

---

### Post by bdoe on 2008-12-20
I concur with what iponeverything said - take a good look at your drivers, particularly proprietary (restricted) drivers. Since some drivers need to run in kernel space, a faulty driver is most likely to cause the kernel to roll over and die.

Read through your system logs (System -> Administration -> System Log is an easy, elegant way to view all your system logfiles) and look for any errors, warnings, or other indications that could point to the source of the problem.

Troubleshooting an event that doesn't log itself or give clear indication of the problem can be messy work for both Linux and Windows. I have another laptop running Vista, and noticed a Windows STOP error being logged nearly every day (usually, the computer, left unattended, would just spontaneously reboot). The information given on the Blue Screen (and in the logs) were just enough to point to improper handling of ACPI events, but was of no help in pointing me to the driver or device responsible for the problem.

By the way, I read your blog, and I think you are spot-on. Linux has the power and ability to overturn the Windows hegemony, but, more than the extra reliance on the CLI to get things done, the lack of real, cohesive documentation from an authoritative source is the one thing that could keep a frustrated Windows user from converting.  I know documentation (and some really well-written how-to guides) are out there, but they are spread all over cyberspace. Perhaps a good start would be to create a Wiki, gather all of the useful data from all over the place, and compile it into an easy-to-read compendium. Ideally, it would be written with the average Joe and Jane as its intended audience, with a basic write-up explaining *why* someone would wish to do the described action, what benefits could be gained by doing so, and what possible drawbacks there are. Each article would also contain a link more advanced readers could follow, pointing to a more detailed technical write-up.

Gaining general acceptance by the Windows community by whatever means are necessary to ease their transition is, in my honest opinion, the best direction Linux - particularly Ubuntu - should be taking. It would be a win-win situation for the entire Linux community, as broader user acceptance would translate to better software support for everyone, forever ending the "Windows can run this and Linux can't" argument once and for all. It could even benefit those in the Windows community who do not wish to convert to Linux, as broader acceptance would force Microsoft to completely rethink their business strategy lest they lose it all; and travesties such as Windows ME and Vista would never happen again.

Okay, enough rambling.  Good luck with hunting your kernel issue. If you ever need any further help, you know where to go.

---

