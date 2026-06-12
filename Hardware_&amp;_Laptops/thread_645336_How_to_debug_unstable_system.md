---
title: "How to debug unstable system"
date: 2007-12-19
forum: Hardware &amp; Laptops
---

### Post by Innomatics on 2007-12-19
I'm started to get a bit tired of the crashes I experience running Ubuntu.  

I'll really like to be able to work out why they happen, but the notebook just locks and the caps+numlock buttons start flashing to indicate kernel panic.  

I have to remove the battery (eek) to get the machine to restart.  Then I can't find any clues as to why the crash occurred.  The demsg log is cleared.  How can I do a 'post-mortem'?

If only Ubuntu was as stable as Windows XP (for me). I'd be happy to help fix it, but don't how to go about debugging random crashes.  I've tried posting a bug in launchpad, but it got ignored - presumably because there is no known attack or solution? 

BTW I don't run compiz.  Std gutsy install in newish notebook with 2GB ram.

---

### Post by crouton on 2007-12-20
More information would be useful...

Does the laptop lock up if you do nothing, ie boots and waits for login?
Have you installed any programs recently, or has this behavior occurred ever since the installation was completed?  (Does it do the same thing on a LiveCD with the same usage pattern?)

What kind of laptop is it (perhaps there are some flags that need to be passed in?)

---

### Post by Innomatics on 2007-12-20
> **crouton said:**
> More information would be useful...

Yes, of course.  I'm not asking ppl to debug my problem for me, but rather how to go about it myself.

> **crouton said:**
> Does the laptop lock up if you do nothing, ie boots and waits for login?

No, it's never done that.

> **crouton said:**
> Have you installed any programs recently, or has this behavior occurred ever since the installation was completed? 

No, I haven't been able to co-relate the behavior with the addition of any new packages.

The problem is because of the 'random' nature of the crashes, it's very hard to deduce which program is the cause.  What I really would like to know if there is a way to find out after the crash what happened?

At least with Windows you got a BSOD which gave you some clues. 

> **crouton said:**
> (Does it do the same thing on a LiveCD with the same usage pattern?)

Live CD doesn't work with this laptop, installed from alternate.

> **crouton said:**
> What kind of laptop is it (perhaps there are some flags that need to be passed in?)

It's a Compal IFL91.  Where do you find such information on which flags to pass in?

---

