---
title: "Powertop doesn't work"
date: 2012-02-07
forum: Hardware
---

### Post by adiasd on 2012-02-07
Hi Folks,

I'm unsing Ubuntu 11.10 and as an attempt to further optimize battery performance I decided to try powertop. I installed the package from software manager and then went to use it with the command:

sudo powertop

However, when I did this I got the following error messages:

Cannot load from file /var/cache/powertop/saved_results.powertop
Cannot load from file /var/cache/powertop/saved_parameters.powertop

These messages are very briefly displayed (I could identify them only  after I directed the output to a file) and then the terminal goes blank  and back to the prompt. Oddly enough after that the terminal isn't  responsive anymore.

Another interesting thing is that the above described behavior happened when I ran powertop while on battery. When I invoke it while on A/C power it does run and show information but that is not the use case I have in mind since I want it exactly to optimize battery usage.

Does anyone have any idea why I can not get meaningful output with powertop while running on battery? Is there another way to invoke it?

Thanks

---

### Post by soulspit on 2012-02-18
Bump. I'm having an identical problem. Additionally, if I unplug my laptop while running powertop, the program quits after a short while, and the terminal is unresponsive (specifically, it seems to work fine but not print any of my keystrokes - I guess powertop somehow has captured keyboard input and not given it back?)

Any thoughts? Running Oneiric Kubuntu with kernel 3.0.0-15. Using powertop 1.97 beta 1.

EDIT:
I removed powertop and installed powertop-1.13, and it ran flawlessly like the good ol' powertop I remember.

---

### Post by adiasd on 2012-02-19
Good hint. I removed Powertop and installed Powertop-1.13 and now it works fine. So it seems there is something wrong with the latest version.

Thanks!

---

