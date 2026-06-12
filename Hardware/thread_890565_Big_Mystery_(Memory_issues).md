---
title: "Big Mystery (Memory issues)"
date: 2008-08-15
forum: Hardware
---

### Post by kitt on 2008-08-15
Hi folks,
	I am having hardware(memory) issues on my laptop (Acer Aspire 5004. AMD Turion ML-34. 245 MB . SiS chipset). However, the issue is so strange and mysterious to me i though i'd share it with you guys in the hope of finding an explanation. ( A bit long though : i;ll try to highlight the important points)

        It all started about a year ago, i installed a new version of Kubuntu (Gutsy) and noticed _very_ frequent application crashes. I had my trusty and extremely stable Kubuntu Fiesty install on another partition. For the first month or so i decided to fix the Gutsy install. I failed and so had to go back to Feisty. It crashed a lot too! It had not done that. ever! I had uptimes of weeks (with standby, hibernate etc.)! So at first i thought its something very wrong with Linux. I tried going back to vanilla ubuntu (Gnome) thinking its  Kubuntu's oft-heard instability troubling me. 
      * Nothing worked. I decided to compile the kernel, thinking that the numerous crashes (avg 1 reboot per hour) meant theres something really messed up with it. And withing seconds of starting the compilation GCC throwed up a message saying "failed compilation due to hardware fault etc."(i dont remember exactly, but it was something on the lines of 'its not GCC's fault.). *
      * So then i realized its something fishy. I mean the kernel is probably the most compiled program in GCC. And i was compiling a stable release too.. definitely not a software bug! *
      ** So i ran memtest 86+ which comes with ubuntu. I had run the program about a year before all these events with no errors. This time, i was shocked to find about 2000 errors listed! Now it all dawned. All those Segfaults were due to bad memory! (I have noticed that all the 'errors' have value 000000200. A;so tests 6,7,8 contribute to all errors)
And i had been harsh on Linux. **
     *** BUT. This story would be a boring one about memory corruption. Real twist comes now: my machine runs OK under windows.  Yes im typing this from a windows. On Linux the mean time for firefox before crashing is 5 minutes.(Segfault). ***
      So whats causing windows to be so resilient to memory problems? Im not saying it runs perfectly, there are application crashes, but its more like 1/hour instead of 1 per $5 minutes on linux. 
       I really, REALLY want to go back to using Linux on this machine.. but its not possible in the current state. Reinstalling is out of question(bad memory again!), forget kernel compile or compiling anything for that matter. 
       So, is there anything i can do to salvage the situation? I know of the bad memory patch, however it needs a kernel compile.

I know its a hardware fault etc, and that u really cant do much about it. But if windows can run, why cant Linux? How is windows able to side-step the bad areas to run OK? Atleast the windows kernel runs fine. I dont have to do reboots etc. Heck, i can even play games smoothly on windows.  Please Help!

PS: Ive tried to 'fix' the problem on my own for about 6 months now. So its not that ive not tried to fix it myself.

---

### Post by Kevbert on 2008-08-15
Windows may work with some defective memory but you may get the occasional random or unexpected crash.  There are two things you can check for which are dust (it can be conductive so carefully clean out with a vacuum cleaner), and badly fitted memory (just remove and refit).
If these don't work then you'll have to try to find the fault by removing one or more memory chips as a process of elimination.  When you think you've found the faulty chip try running just that chip in one socket and then another as it may still be due to the memory being poorly seated.
Make sure you're well earthed when you do this as the devices are static sensitive.

---

### Post by kitt on 2008-08-15
Hi Kevbert,

Thanks for the reply. But in case i missed, this is a laptop, so opening it etc may not be so straight forward. 

Also, what can possibly explain the order of magnitude more stability of windows as compared to Linux on this broken machine?

---

### Post by Kevbert on 2008-08-15
Having the same problem myself in the past it can happen.  I don't know why.
As it's a laptop there's probably a compartment that can be easily accessed by a couple of screws (my Acer laptop has this).  Watch out if you decide to change the memory as this can be expensive.

---

