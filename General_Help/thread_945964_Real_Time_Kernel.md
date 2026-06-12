---
title: "Real Time Kernel"
date: 2008-10-12
forum: General Help
---

### Post by Kyle54 on 2008-10-12
Is it possible to have a REAL TIME kernel in Ubuntu Hardy? (NOT Ubuntu Studio)

Ubuntu Studio sucks. The file system is different enough that drivers for wi-fi cards with instructions for Ubuntu installation DO NOT work on Studio.

I just want the kernel. Normal Ubuntu Hardy, with the real-time kernel for low-latency audio. Possible? Can i just install it after installing normal Ubuntu?

Why don't I want Studio? Because my Wi-fi card is automatically recognized in standard Ubuntu Hardy. And it ISNT in Studio.

If it is possible to add the realtime kernel and such, it wont kill the support for my wi-fi, will it?

---

### Post by mrowth on 2008-10-12
> **Kyle54 said:**
> Is it possible to have a REAL TIME kernel in Ubuntu Hardy? (NOT Ubuntu Studio)

Ubuntu Studio sucks. The file system is different enough that drivers for wi-fi cards with instructions for Ubuntu installation DO NOT work on Studio.

I just want the kernel. Normal Ubuntu Hardy, with the real-time kernel for low-latency audio. Possible? Can i just install it after installing normal Ubuntu?

Why don't I want Studio? Because my Wi-fi card is automatically recognized in standard Ubuntu Hardy. And it ISNT in Studio.

If it is possible to add the realtime kernel and such, it wont kill the support for my wi-fi, will it?

I installed the "linux-rt" package on a plain old Kubuntu Heron alongside the generic kernel, then added 
@audio - rtprio 99
@audio - memlock 250000
@audio - nice -10
to "/etc/security/limits.conf". (I don't know if those are the ideal values.)

---

### Post by Kyle54 on 2008-10-12
> **mrowth said:**
> I installed the "linux-rt" package on a plain old Kubuntu Heron alongside the generic kernel, then added 
@audio - rtprio 99
@audio - memlock 250000
@audio - nice -10
to "/etc/security/limits.conf". (I don't know if those are the ideal values.)

Sorry what does that mean? Does that mean YES there is such thing, and its as effective as it is in Studio?

and you didnt experience any other hardware problems as a result, right? the wi-fi for me is vital.

again, for standard ubuntu, my card is plug-and-play. for studio, it isnt, and its absolute suck. so is it possible to install the realtime kernel in Ubuntu NORMAL (keeping the plug-and-play support), and have the great performance that Studio offers, without having to install Ubuntu Studio itself?

---

### Post by Spaceman9 on 2008-10-12
If you're going to compose music you could just install the Ubuntu Studio Audio Package. it's in the repos and it will install the rt kernel without installing all the other parts of Ubuntu Studio. 

If you just want a real time kernel install linux-rt. It's in the repos. That will install everything the rt kernel needs to work.

---

### Post by mrowth on 2008-10-12
> **Kyle54 said:**
> Sorry what does that mean? Does that mean YES there is such thing, and its as effective as it is in Studio?
Yes, there is such a thing. Installing the "linux-rt" package will give you the latest available realtime kernel, restricted modules, etc.

The "ubuntustudio-audio" package recommends that same "linux-rt". It and "ubuntustudio-audio-plugins" are useful metapackages that pull in all sorts of audio apps without adding the Studio branding and look'n'feel; you can add those through other ubuntustudio-* packages if you want to fully transform an ordinary Ubuntu into a "Studio" Ubuntu. I always thought the results would be the same... that it's not in any way inferior to an UbuntuStudio installation from DVD.

> and you didnt experience any other hardware problems as a result, right? the wi-fi for me is vital.
Sorry, I don't know about your wi-fi. Mine is plug-and-play, too, but I've never used it while having an rt kernel installed. (Could plug the card back in and tell you tomorrow if it's recognised, if that's any help... don't have a network to connect to with it, though.)

However: After an upgrade to a dual core CPU realtime kernels became very unstable until I added "noapic" to the kernel boot parameters in menu.lst (for unrelated reasons). The mouse would freeze, network (wired) die, screen go blank, etc.

> again, for standard ubuntu, my card is plug-and-play. for studio, it isnt, and its absolute suck. so is it possible to install the realtime kernel in Ubuntu NORMAL (keeping the plug-and-play support), and have the great performance that Studio offers, without having to install Ubuntu Studio itself?
I'd say give it a try. It won't remove the old kernel, after all.

---

### Post by goulven on 2008-10-13
Hello, (I'm a French user, sorry for my bad English)
Since few days I'm trying to configure my new sound card (Audiofire4), with ffado drivers.

Now it's work but i can't run qjackctl in realtime mode.
My configuration:

Ubuntu 8.04 with new kernel : 2.6.24-19-rt
(i did it whith sudo apt-get install linux-rt)

i did this changes to my /etc/security/limits.conf
    @audio  -  rtprio   99
    @audio  -  nice     -10
    @audio  -  memlock  100000

I have only 256Mo of RAM, that's why i set memlock to 100Mo

But i don't know if the real time is enable.

in a terminal, when i wrote:
**uname -r**
the return:
**2.6.24-19-rt**

**lsmod | grep realtime**

I should have the two module loaded "realtime" and "commoncap", but i have nothing.

**cat /etc/default/realtime | grep 29**
return:
**PARAMETERS="gid=29"**

Can you help me? 
My audiofire4 work fine with no realtime, when i enable the realtime, qjackctl tell me:

[I]18:43:42.329 /usr/bin/jackd -R -dfirewire -dhw:0 -r48000 -p1024 -n3
18:43:42.332 JACK was started with PID=7440.
18:43:42.368 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
no message buffer overruns[/I]

Maybe i haven't got enough ram?
thanks.

---

### Post by mrowth on 2008-10-15
Sorry, I wish I could help you.

> **goulven said:**
> in a terminal, when i wrote:
**uname -r**
the return:
**2.6.24-19-rt**

**lsmod | grep realtime**

I should have the two module loaded "realtime" and "commoncap", but i have nothing.

Neither do I. Should I really? JACK starts in RT mode anyway, with 5.33 msec latency, 128 frames/period. (Actually, it starts in RT mode even when I boot into the generic kernel. But only if I've already installed the RT kernel.)

> **cat /etc/default/realtime | grep 29**
return:
**PARAMETERS="gid=29"**

cat: /etc/default/realtime: No such file or directory

Hmm...?

---

