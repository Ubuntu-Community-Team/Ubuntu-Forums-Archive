---
title: "Dual boot with Vista and Ubuntu 8.10 (Vista installed first)"
date: 2008-11-10
forum: General Help
---

### Post by i_baked_cookies on 2008-11-10
I've had Vista installed for a while now - no big problems with it yet, I'm a more casual computer user :)  I do like to tinker though, and I want to see how Linux runs and works on my laptop.  I read a few tutorials about dual-booting Vista and Linux, and it all sounds way too easy :)

1. repartition HD to fit Ubuntu
2. Install Ubuntu
3. Upon starting computer, select operating system (Vista or Ubuntu)

Is there something important that I'm missing?  And can I install/uninstall Ubuntu with NO affect to my Vista system or files?

Thanks in advance.

---

### Post by caljohnsmith on 2008-11-10
Check out Herman's website for a great [step-by-step guide]("http://www.herman.linuxmaniac.net/p22.html") for installing Ubuntu. Let me know if that helps. :)

---

### Post by kernelhaxor on 2008-11-10
That is all there is to it.  Just delete the Ubuntu partition if you wish to get rid of Ubuntu in the future.  Installing Ubuntu on a different partition will not affect Vista.

---

### Post by i_baked_cookies on 2008-11-10
Thanks guys... I'll be doing this right now!

---

### Post by TeXtonyx on 2008-11-10
I think you should resize the Vista partition with Vista rather 
than with the Ubuntu tool later during the install. Then you can
choose during the live cd install, 
'install to largest free space (guided)' which will use the
unallocated space you created with shrinking the vista partition
earlier. I think this is safer than resizing "on the fly".

---

### Post by TeXtonyx on 2008-11-10
> **kernelhaxor said:**
> That is all there is to it.  Just delete the Ubuntu partition if you wish to get rid of Ubuntu in the future.  Installing Ubuntu on a different partition will not affect Vista.

If he chooses the default on installing grub to the MBR, and he
'wishes to get rid of Ubuntu in the future', then he will no
longer be able to boot Vista. I think the OP will consider this
to be affecting Vista. He can fix that with the Vista install cd,
but some people don't get those issued, instead they get OEM
recovery disks which don't permit executing the bootrec command.

The OP can avoid installing grub to the MBR in Step 7, Advanced,
by choosing the /boot partition from the drop down menu. There 
is a program, Easybcd, for Vista, which puts Ubuntu on the 
boot menu. Then if he removes Ubuntu, there is no PITA situation.
And if Vista has a problem, the OP can still boot Ubuntu with 
the Super Grub Disk.

---

### Post by Citizenview on 2009-03-12
I should like to inform the Ubuntu developers here that whereas it is easy to install Ubuntu in an XP machine, it is quite another story in a Vista machine. I have tried everything I know which is not much and I am stuck at what looks like a X terminal awaiting CLI. I hired an "expert" for $150/hr. and he walked me through the CLI and part of this was a bit scary because he made me to go to the root but no harm done, only FAILURE to make Ubuntu work. Then, he wanted me to buy "a block of 4 hours" and I politely declined.

He said that the Ubuntu had something to do with the Nvidia card drivers. I am glad that I did not pursue this because I am not unhappy with my new Vista machine yet. Besides, I already have Ubuntu on six different machines. I also use Macs.

So, the question of Vista and Ubuntu remains clearly open and unanswered. I get stuck at an X terminal every time I start Ubuntu from within my HDD or from a LiveCD, or from an USB stick. I'd like to have Ubuntu on my Vista machine and your help will be highly appreciated.

---

