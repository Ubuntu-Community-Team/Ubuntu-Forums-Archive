---
title: "Toshiba L645 - ACPI problem in 10.10"
date: 2010-12-30
forum: Hardware
---

### Post by dustinmoorman on 2010-12-30
Good day everyone. I have found that nearly everything  works on my Satellite L645, the RTL8188CE driver had to be installed from the website, but all else is good except for the battery life indicator. I know some of you toshiba fans have had the same problem, but with more modules not working than just the battery life, but I'd like to know some possible fixes or ideas among you guys, to help myself and anyone else with this cool little L645.

Some things that I've noticed, are that acpi does not notice the battery as being installed, and refers to it as not being present.

```
root@dustin-Satellite-L645:/proc/acpi/battery/BAT1# cat info
present:                 no

```Any help would be greatly appreciated. It always believes it is plugged in to AC power. I am also curious if anyone has gotten this to work, apparently, linux kernels 2.6.x have "included" toshiba acpi packages. Not sure about this, this information is found here:

[http://memebeam.org/toys/toshibaacpidriver](http://memebeam.org/toys/toshibaacpidriver)

The article describes the directory *toshiba* that will appear under */proc/acpi*.

I have only begun research into this problem for these L645's, but I will update my own thread when I come across progress or a solution.. Thanks, I hope we can all be helped by this. Let me know if you own similar Toshiba laptop newborns (purchased in 2010), and if you experience any problem with yours, as i have with mine.

---

### Post by dustinmoorman on 2010-12-30
Another weird notice of mine, is that BAT0 has usually been the first (and only) battery recognised by acpi, in my experience. However my machine is defaulting to BAT1. 

Thanks for reading, just posting any information I can as I delve in to this.

---

### Post by momod on 2011-03-09
I have same problem...
do you have solution for that??

---

### Post by evPaseo on 2011-04-15
I've got the same problem. Guess there's no fix yet?

---

### Post by thuci on 2011-05-15
I have the same problem mine is toshiba satellite L655

---

### Post by evPaseo on 2011-08-07
Eureka!! I found a solution to this problem and cured my Satellite L645!  The instructions found in the link below describe the process of building a custom kernel.  The result is that the battery is recognized and appears to be properly controlled (power management, battery meter, etc.).  This process takes a while to complete, but if I can figure it out anyone can.  Thanks to Faheem and his article at techinterplay.com:

[http://techinterplay.com/fix-toshiba-battery-issue-linux.html]("http://techinterplay.com/fix-toshiba-battery-issue-linux.html")

---

