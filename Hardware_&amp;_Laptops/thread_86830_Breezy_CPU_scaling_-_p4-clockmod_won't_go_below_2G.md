---
title: "Breezy CPU scaling - p4-clockmod won't go below 2GHz"
date: 2005-11-06
forum: Hardware &amp; Laptops
---

### Post by shof2k on 2005-11-06
Folks,
Sorry if I'm stating what everyone knows, but I thought I'd share this to save anymore ](*,) 

I've noticed there are a number people having issues with cpu scaling using the p4-clockmod module.  This was working sucessfully in Hoary on my Intel(R) Celeron(R) CPU 2.00GHz, but failed to work in Breezy.  I had the correct cpufreq modules, p4-clockmod, and sysfs, but could not get powernowd to work even though it was running!  

Then I used dmesg and saw the following everytime i added p4-clockmod
```

p4-clockmod: has N60 errata - disabling frequencies below 2.0 GHz
[4320437.470000] p4-clockmod: disabling frequency 250000
[4320437.470000] p4-clockmod: disabling frequency 500000
[4320437.470000] p4-clockmod: disabling frequency 750000
[4320437.470000] p4-clockmod: disabling frequency 1000000
[4320437.470000] p4-clockmod: disabling frequency 1250000
[4320437.470000] p4-clockmod: disabling frequency 1500000
[4320437.470000] p4-clockmod: disabling frequency 1750000
[4320437.470000] p4-clockmod: P4/Xeon(TM) CPU On-Demand Clock Modulation available

```
  
Googling "n60 errata p4-clockmod", showed the following bug report [http://lists.ubuntu.com/archives/kernel-bugs/2005-April/000742.html]("http://lists.ubuntu.com/archives/kernel-bugs/2005-April/000742.html").  

Basically the module is now patched to prevent any throttling below 2Ghz, which won't help me because my laptop runs at that.  Also, since all the scaling utils I know (cpufreq, emifreq, powernow) make use of this module, they become equally redundant :(

Since I didn't suffer the N60 issue in Hoary, does anyone know how to get the unpatched module or is there another way around this?  Without useful scaling, this puts Breezy at a distinct disadvantage, not good with Vista round the corner.

Lets wave some linux magic and sort this out :)

---

### Post by Spiderdba on 2005-11-08
I have the same problem, and didn't find any solution anywhere. :confused: 
This is quite annoying, since P4 is not really an "energy saving" CPU. After upgrading to Breezy I can run my laptop on battery for less than an hour (it was more than two hours with Hoary with CPU running between 700  and 1400).
Is there anyone who can tell some workaround for this??

---

### Post by djkork on 2005-11-21
see my replies at 
[http://www.ubuntuforums.org/showthread.php?p=509795#post509795]("http://www.ubuntuforums.org/showthread.php?p=509795#post509795")

---

### Post by Maverick911 on 2005-11-21
I've got the same problem. 

Can someone detail how to recompile p4-clockmod without the patch so that I could at least try it on my laptop? I've searched the forums and google but can't seem to find anything. ](*,) 

I don't know where to begin.
Thanks in advance for any help. These forums have been a godsend in helping me get linux running on my laptop.

HP zx5369cl
Pentium 4, 3.2GHz
Ubuntu Breezy

---

### Post by Paul Casey on 2005-11-21
[QUOTE=shof2k]Folks,
Sorry if I'm stating what everyone knows, but I thought I'd share this to save anymore ](*,) 
[/QUOTE]

wanting to understand the issue... is it [cpu scaling] a power saving mode for longer battery life on the laptop pc?   thanks.  have not used Ubuntu on laptops yet and am doing homework for my first laptop with it.

---

### Post by shof2k on 2005-11-22
In theory yes, by limiting cpu scaling and voltage you reduce the power consumption and give a longer battery life. However battery life is also dictated by screen usage, HD usage etc.

In this case p4-clockmod only does cpu scaling and not voltage scaling so the savings aren't as great as expected.  I want this module as it helps reduce fan usage and gives me less noise to worry about.

Hope that helps,

---

### Post by shof2k on 2005-11-22
Thanks for the reply.  I was worried that this needed a kernel recompile :(

Personally it would've been better to deliver p4-clockmod without the patch and tell N60 affected users to remove p4-clockmod.

---

### Post by shof2k on 2006-01-09
Update.
I've took the plunge and did a kernel recompile.  Along with a nice system, this gave me a working p4-clockmod, very nice.

If there is demand, I'll put it on this post :)

---

### Post by linuxfanatic1024 on 2006-01-13
[QUOTE=shof2k]Thanks for the reply.  I was worried that this needed a kernel recompile :(

Personally it would've been better to deliver p4-clockmod without the patch and tell N60 affected users to remove p4-clockmod.[/QUOTE]
What I would prefer is a module option to disable the patch and force it to work anyway. I have the same problem on my Toshiba Satellite A65-S126 w/ 2.8 GHz Celeron. I really wish the patch had never been applied.

---

