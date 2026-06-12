---
title: "Toshiba P100 overheating and only one processor recognised"
date: 2006-08-15
forum: Hardware &amp; Laptops
---

### Post by Martenii on 2006-08-15
Hi there,

I have installed Kubuntu 'Dapper' onto my Toshiba P100 laptop and have a few problems. The computer boots into Kubuntu ok and I think that my issues may be related more to the OS than to the desktop gui, hence my posting in this forum.

The first and probably most important is that the computer is getting very hot, I imagine that this is because the OS in not controlling the cooling fans as efficiently as needed. I was using kubuntu for about two hours last night before I noticed the heat comming from the keyboard and just to the left of the touchpad, I halted the system before it became unstable. This does not occur in Windows XP the shipped OS.

Only one core of the Centrino Duo, and only half (1G)of the system RAM are recognised.

There is a sound card issue, but this seems to have been dealt with in these forums and I will attempt to fix that once I have fixed the overheating.

I am sorry I have not provided much in the way of technical information, I am totally new to linux on a laptop and really don't know where to start with this.

I originally posted this here:
[http://ubuntuforums.org/showthread.php?t=236454](http://ubuntuforums.org/showthread.php?t=236454)
and think maybe my title was too vague.

Thanks in advance for any help you can offer.

---

### Post by halfvolle melk on 2006-08-15
Hi,
Check out this thread:
[http://www.ubuntuforums.org/showthread.php?t=85917](http://www.ubuntuforums.org/showthread.php?t=85917)
In your case I think linux-686-smp is the way to go. Another thing that I think and do not know to be true is that the default 386 does not allow CPU frequency scaling whereas the 686 does, so
```
sudo apt-get install linux-686-smp
```
might solve both issues.

---

### Post by Martenii on 2006-08-15
Thanks halfvolle melk for your reply; I will try as you suggest and report back.

Many thanks again :)

---

### Post by Martenii on 2006-08-16
Ok, I installed the smp kernel and rebooted.  The Processors and ram were recognised, but processor 0 was reporting 100% usage constantly while processor 1 reported a load more in line with the systems actual use.  The overheating problem seemed to not have improved, ie: the fans don't seem to run and things got very warm so I halted again.

I then booted to knoppix 4 that I had lying about the place and it recognised the processors and ram with both cores behaving more like I would expect.  The fans seemed to work, but never to full speed and the system gradually started to overheat.  So again, another system halt.

I have a copy of Gentoo 2006.0 live kicking around so I'll give that a go.

Bummer.

---

### Post by Martenii on 2006-08-19
Ok, I ran the Gentoo live cd and everything was fine bar the overheating.  It seems that toshiba have a non compliant acpi.  Bummer.  I bought this notebook 'cos linux support was supposed to be good.  I wonder what 'bad' is like?  When I get time I'll give the 'no acpi' option to grub, this is supposed to allow the system fans to run at 100% permanently.  Not elegant, I may at least be able to run *nix on my system - and be able to get properly started to sort this out.  This is a major annoyance though, all my data is  on my *nix desktop system, and I wanted the lappy and desktop to talk to each other using Korganiser.

I'll be back.

---

### Post by rax_m on 2006-11-06
Hi Martenni, 

Did you ever get your issues with your Toshiba sorted out?

I just bought the P100-429 and am having the same overheating issues. 

Cheers
Rax

---

### Post by bonzini on 2006-11-08
Hi folks,

Another (but happier) Toshiba user here.  Mine's a bit older, a PSA70C, which has a dual core pIV.  Ubuntu recognizes both CPUs, fans go up and down, etc.

I would have to say that I have never had problems like you two have experienced, right from ubuntu breezy.  I had wireless problems with breezy but eventually got that sorted out.  Since then things seem quite good, with the exception of never being able to get fglrx to completely work.

A couple of ideas:

Toshiba Japan has some limited Linux stuff on their site.  Worth a look, though it's probably out of date.

Do a search for toshiba in package manager and see if anything pops out at you.  There is some acpi stuff there if I'm not wrong.

---

### Post by rax_m on 2006-11-08
Thanks for the reply.. 
I'll give it a go. Unfortunately I can only do it this wkend, as I'm away from home during th week (and already have two other (work) laptops I have to lug around) :o/

Rax

---

### Post by rax_m on 2006-11-10
Hmmm... maybe I've been a muppet.

I noticed today that the fan IS coming on, on my Toshiba. 
Just a lot less frequently then when windows is running...

should I be worried?

On another note, I managed to get my nvidia drivers installed

I'm quite impressed by the support for this laptop actually.
Even the keys normally accessed through the function button (e.g. screen brightness, mute/unmute) work well.

---

