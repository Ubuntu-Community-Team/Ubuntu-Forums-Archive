---
title: "Shutting laptop issue"
date: 2008-05-10
forum: Hardware
---

### Post by cowboy_mcd74 on 2008-05-10
Hi,

I just installed Ubuntu a few days ago, and so far, I'm loving it. I was expecting to have to do a lot of configuration to get it working, but so far it's been great!

There's really only one serious issue: whenever I shut my laptop lid and re-open it, the screen messes up and fills with tons of crazy multicolored blocks. The OS is still running, I can tell because I can click blindly and eventually shut it down; but it becomes unusable unless I restart!

This issue doesn't happen if I have it suspend when I close it, or if the screen shuts off on its own because of idling.

I've searched the forum for this problem, and all that came up was problems with suspending: but I don't have a problem with that.

Thanks in advance

Also, my computer is a Thinkpad T60, with all the standard T60 hardware

---

### Post by roma2 on 2008-05-10
It's an ACPI bug. [This]("http://www.thinkwiki.org/wiki/ThinkWiki") website is an awesome resource on Thinkpads (which I use myself).

---

### Post by cowboy_mcd74 on 2008-05-10
Well, after reading that, it seems the best way to fix this problem is to run APM instead of ACPI....

Anyone know if this is a good idea? If so, how exactly would I go about doing this? (I actually just tried with instructions possibly based on an older version of Ubuntu, and ended up having to re-install the OS...)

Or, where else in the ThinkWiki would it describe my problem? The best I can find is the part where it explains APM vs. ACPI, but that says "blank screen" should work with T60s...so I assume it's not talking about when I shut the laptop.

Also, could it be a problem with the ATI X1300 graphics card not being supported?

---

### Post by roma2 on 2008-05-11
Well, I have an Nvidia Quadro in my laptop, an 8800GTX in my desktop, and Intel chips at work, so I have no experience whatsoever with ATI cards in Linux. 

From what I understand, ACPI is supposed to give you better battery performance when properly configured, but I haven't finished mine yet. It still hangs on resume from suspend after updating the BIOS. Have to start digging around the ACPI configs next.

Check out this URL to enable APM. See if that helps.
[http://www.thinkwiki.org/wiki/How_to_make_APM_work]("http://www.thinkwiki.org/wiki/How_to_make_APM_work")

This URL explains the caveats of ACPI setup, and is the one I am working through on my free time to fix my T61.
[http://www.thinkwiki.org/wiki/How_to_make_ACPI_work]("http://www.thinkwiki.org/wiki/How_to_make_ACPI_work")

---

### Post by cowboy_mcd74 on 2008-05-13
Well, I solved the problem, though it's a bit of a dumb way to do it...

I just installed Gutsy instead of Hardy. Other than having to map a few more keys (which really isn't that hard...), and having a few packages not work (had to use JRE 5 instead of JRE6), it seems to work flawlessly.

You'd think, if a problem was solved in an old version, it'd stay solved in a new one, right?

Oh well; I'll just wait until Intrepid (that's the next one, right?) comes out, and see if it's fixed then. =D

---

### Post by roma2 on 2008-05-13
> **cowboy_mcd74 said:**
> and having a few packages not work (had to use JRE 5 instead of JRE6)

You can probably update some of that from backports. Thanks for the update as well, I am considering rolling back to another version myself as this ACPI issue is quickly becoming an annoying deal-breaker for me.

---

