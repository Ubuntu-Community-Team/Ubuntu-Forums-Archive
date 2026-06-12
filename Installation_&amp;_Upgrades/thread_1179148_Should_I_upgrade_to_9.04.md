---
title: "Should I upgrade to 9.04?"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by oxf on 2009-06-05
OK I know there may be no definitive answer to this but....! I'm about to reinstall and move to Jaunty 9.04. (Running Hardy  right now) I did briefly try Intrepid and reverted to Hardy because I had problems with slow web browsing.  

I've been reading around a bit and see there opinion varies a bit on this question.  From what I've read there seems to be some questions around display drivers. In my Laptop I have ATI Radeon XPRESS 200M 5955 (PCIE). In my desk top its Nvidea. 

Under Hardy I have had a minor problem on laptop with handling very large intensive PDFs (scrolling causes freeze up). I've been told I can resolve that by switching to the open source drivers. But havnt yet in anticipation of moving to 9.04.

Getting my Broadcom wireless card working took a little bit of work on the laptop due to the BC43XX issue but eventually did it.

Other issues: I've heard 3D/compiz problematic under Jaunty? I dont use these so not an issue.

Boot up time/overall speed under Jaunty? And any other things I should be aware of or consider in upgrading to Jaunty? Essentially should I do it??
Any thoughts appreciated!

---

### Post by Mark Phelps on 2009-06-05
You won't be able to get ATI restricted drivers under Jaunty because AMD/ATI dropped support for your video chip (along with lots of others).

Your best bet would be to boot from a LiveCD and see how well the PC works with detecting the hardware and installing the drivers before you do an upgrade.  If there was a simple, one-click rollback mechanism, I'd say go ahead an upgrade.  But as you've probable already read, there's no such thing and folks are having a lot of problems after upgrading.

---

### Post by matamoscas on 2009-06-08
Hi Mike,

I think it depends on your hardware. I tried 9.04 on my laptop, and it ran dreadfully slow, so I went back to 8.04.

It looks great -- but I need better hardware, that I am now in the process of buying. Not new, but *newer*. =)  My laptop is over 5 years old, so it can't hack it anymore.

If your hardware is fairly modern, I'd say bought within the last 1-2 years, give it a go.

---

### Post by oxf on 2009-06-08
> **matamoscas said:**
> Hi Mike,

I think it depends on your hardware. I tried 9.04 on my laptop, and it ran dreadfully slow, so I went back to 8.04.

It looks great -- but I need better hardware, that I am now in the process of buying. Not new, but *newer*. =)  My laptop is over 5 years old, so it can't hack it anymore.

If your hardware is fairly modern, I'd say bought within the last 1-2 years, give it a go.

Hi..
Well my desktop is under a year old (Acer Aspire L100). Booting from the Live CD looked fine so I went ahead and installed. Thats where I'm stuck! Its boots but the display is blank.I hear the Ubuntu start up music so it is booting but there no display. I also get an error message after grud screen that says "MS Bios bug..unable to connect to IO-APIC"  Life sucks ! :frown:

---

### Post by zubin71 on 2009-06-08
9.04 is definitely a really good option. i have not come across any problems in jaunty. i use a lenovo notebook and everything works just fine!

---

### Post by markbuntu on 2009-06-08
Well, Jaunty will only be supported for 18 months from release so you will be forced to upgrade sooner than if you stick with Hardy. The open source drivers for your 200M are much improved in Jaunty and will give you full accelerated 2D and 3D but will be even better with Koala. The broadcomm issues have been mostly fixed in the kernel. Boot time and overall speed is far faster with Jaunty but problems with sound are rampant, especially with laptops. Koala will be out in 4 months...you might want to wait

---

