---
title: "Resolution problems Kubuntu 10.04 on Acer 7552G-5430 with Radeon HD 6650M"
date: 2011-04-17
forum: Hardware
---

### Post by arch0njw on 2011-04-17
The instigating problem is an incorrect resolution.  The screen is 1600x900 but the resolution used is 1152x864.

I am having a really hard time with this one.  I have tried configuring the open source driver as well as the proprietary driver.  In both cases, "aticonfig" reports to me that "No supported adapters detected".

Here is the relevant line from lspci:
```
02:00.0 VGA Compatible controller: ATI Technologies Inc Device 6741
```



Of course, I'm a little confused why that says "6741" when the specs are that this is supposed to be a "6650M".  I'm hoping that is merely a device code as apposed to the model it believes this is.

I also tried starting from a Ubuntu 10.04 live USB and it could not configure the proper resolution either.

I really need help on this one.  Quite lost.

---

### Post by yogi1983 on 2011-04-20
it might take a bit but there will be answers. i have the same problem with a HD 6370m.
Ciao

---

### Post by arch0njw on 2011-04-21
> **yogi1983 said:**
> it might take a bit but there will be answers. i have the same problem with a HD 6370m.
Ciao

I know I'm about to speak sacrilege, but I also filed a bug against the proprietary drivers which don't seem to pick up the card either.  Seems like this is just one of those things.  Shame on me for not doing my homework.  (At least I have a Win7 partition to run off... for now.)

---

### Post by niponbharali on 2011-04-21
I have also faced the problem of screen resolution in kubuntu in my Acer desktop.It will be nice,if some expert help in fixing the issue.

---

### Post by arch0njw on 2011-04-21
Please help them help us.

For anyone responding to this with similar issues, run "lspci" at the command line and either **post** _video controller line_ (if you know which one) **or** the _entire output_.

This is going the help collect device information.  Hopefully this will contribute to resolving the issue.

I have submitted a bug for this.  We'll see what happens from this point.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/768340](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/768340)

---

### Post by alanjleo on 2011-06-07
I'm having the exact same problem, would an older version of Ubuntu or a kbuntu solve this? or are we just stuck?

I have this after I lspci

[FONT=Courier New]...
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)[/FONT]
[FONT=Courier New]...
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6741[/FONT]

---

### Post by arch0njw on 2011-06-07
> **alanjleo said:**
> I'm having the exact same problem, would an older version of Ubuntu or a kbuntu solve this? or are we just stuck?

I have this after I lspci

[FONT=Courier New]...
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)[/FONT]
[FONT=Courier New]...
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6741[/FONT]

Still stuck-a-rooney-tooney, my friend.

---

### Post by alanjleo on 2011-06-08
Will these drivers work on a Fedora distro? I'm just looking for any *nix os.

Also, I was talking to a guy who's seems to know most things about Linux and he suggested "Sandy bridge" for the drivers? Anybody have any experience and/or success installing these drivers and getting them to work?

Thanks!

---

### Post by mastablasta on 2011-06-09
have you tried:
 
- Upgrading Ubutnu to latest release (or run the latest release live)?
- install new drivers found on ATI website?

---

### Post by arch0njw on 2011-06-09
> **mastablasta said:**
> have you tried:
 
- Upgrading Ubutnu to latest release (or run the latest release live)?
- install new drivers found on ATI website?

I tried the LiveCD for 11.04 with no change.

I tried the latest drivers from ATI and no change.

---

### Post by arch0njw on 2011-06-09
> **alanjleo said:**
> Will these drivers work on a Fedora distro? I'm just looking for any *nix os.

Also, I was talking to a guy who's seems to know most things about Linux and he suggested "Sandy bridge" for the drivers? Anybody have any experience and/or success installing these drivers and getting them to work?

Thanks!

I'm not sure if this will work on Fedora.  I haven't tried it yet, but it should be pretty easy to either make a live USB or CD and give that a try.  Worst case you install the OS in a quick and dirty fashion to see if it works.  Have you checked the Fedora forums?

"Sandy bridge" is an Intel chipset, not drivers.

---

### Post by mastablasta on 2011-06-09
what does the xorg configuration file say? perhaps you can change the resolution there. though i find it strange that latest ATI driver is not working propperly.

---

### Post by arch0njw on 2011-06-09
> **mastablasta said:**
> what does the xorg configuration file say? perhaps you can change the resolution there. though i find it strange that latest ATI driver is not working propperly.

1. Your handle is *awesome*

2. What xorg.conf?  New Ubuntu doesn't do that anymore...  Yeah, yeah... I know.  I can build my own from scratch (*yack*).  Would be nice if these drivers worked instead.  I'm sure I'll get to that "at some point" when I feel like hacking up a file.

---

### Post by alanjleo on 2011-06-11
I installed Fedora 15 and it worked! and you just login with "classic gnome with compiz" and you don't have to deal with that funky gnome 3 thing.Its not Ubuntu, but its close enough for me[B]!

[/B]+1 on the **mastablasta** handle

---

### Post by Fubunt2 on 2011-06-11
kinda having the same problem
ubuntu 10.10
have a gtx 295 
acer s243hl
my current resolution is 1300x700
in windows my resolution was 1920x1080
how do I install the latest driver from nvidia?
how do I change the resolution to 1920x1080?

:!:

---

### Post by arch0njw on 2011-06-11
> **alanjleo said:**
> I installed Fedora 15 and it worked! and you just login with "classic gnome with compiz" and you don't have to deal with that funky gnome 3 thing.Its not Ubuntu, but its close enough for me!

Nice!  I'll have to give that a try.

---

### Post by arch0njw on 2011-06-11
> **Fubunt2 said:**
> kinda having the same problem
ubuntu 10.10
have a gtx 295 
acer s243hl
my current resolution is 1300x700
in windows my resolution was 1920x1080
how do I install the latest driver from nvidia?
how do I change the resolution to 1920x1080?


Here is a set of instructions I found for doing that.
[http://ubuntuguide.net/how-to-install-nvidia-graphics-driver-in-ubuntu-10-10-maverick-meerkat](http://ubuntuguide.net/how-to-install-nvidia-graphics-driver-in-ubuntu-10-10-maverick-meerkat)

For the best help, I recommend you start a new forum thread so people can find your issue more easily and assist you.

---

### Post by arch0njw on 2011-06-13
There appears to be a compile-your-own solution that works on Debian.  I have not tried this yet and it is for an ATI 6700.  I thought I would share the link for anyone wanting to try this under Ubuntu:

[http://enc.com.au/2011/06/debian-linux-on-hp-dv6-6023tx/](http://enc.com.au/2011/06/debian-linux-on-hp-dv6-6023tx/)

---

### Post by arch0njw on 2011-06-14
> **arch0njw said:**
> I tried the LiveCD for 11.04 with no change.

I tried the latest drivers from ATI and no change.

I need to correct this statement...  I must have tried 10.10.  I tried Ubuntu 11.04 and it worked.  I plan to try Kubuntu 11.04 and see if I have the same success.  That would be nice.

---

### Post by arch0njw on 2011-06-14
> **arch0njw said:**
> I need to correct this statement...  I must have tried 10.10.  I tried Ubuntu 11.04 and it worked.  I plan to try Kubuntu 11.04 and see if I have the same success.  That would be nice.

And it would seem that Kubuntu 11.04 also works.  Huzzah!  I am experiencing some other minor issues, but nothing to do with screen resolution -- that much is very nice.

---

