---
title: "&quot;Instant-on&quot; OS like splashtop?"
date: 2008-09-16
forum: Hardware
---

### Post by Ck.asdf on 2008-09-16
I was wondering if there might be an OS I could install to the hard drive, to be able to get close to the instant-on speeds of OSes like Splashtop, which I've read is installed to the BIOS.
Apps I'd want to be able to use would be:

*Firefox
*Media player (I'm not too picky)
*IM (Pidgin preferred, though I could use meebo through Firefox)
*Text editor (something like gedit would be fine)
*terminal/console

And of course, I'd want the wireless and Ethernet to be supported, otherwise it'd be a little pointless most of the time for me to use this.

---

### Post by Vivaldi Gloria on 2008-09-16
> **Ck.asdf said:**
> I was wondering if there might be an OS I could install to the hard drive, to be able to get close to the instant-on speeds of OSes like Splashtop, which I've read is installed to the BIOS.


Impossible with a regular bios because you lose around 5 secs with the bios just to reach the bootloader. Then you'll need at least 10-15 secs to boot the system even with the lightest possible OS, and the fact that you want firefox puts such light OS out of reach. I doubt you can get an OS with a full featured desktop to boot in less than 30 secs.

---

### Post by RawMustard on 2008-09-16
> I doubt you can get an OS with a full featured desktop to boot in less than 30 secs.
Hehehe! How about debian base install with xorg-xserver and fluxbox?

Boots in 17.5 seconds here :)

---

### Post by mikjp on 2008-09-16
Try Minix. Or FreeDOS.

BTW, OO.org is not a text editor. It is a word processor + other office software. If you want a lightweight word processor, try Abiword.

mikko

---

### Post by insane_alien on 2008-09-16
closest you can get is keep your machine on but suspend to RAM. its not possible on generic hardware as there is all sorts of stuff the OS has to do to get up and running.

---

### Post by Vivaldi Gloria on 2008-09-16
> **RawMustard said:**
> Hehehe! How about debian base install with xorg-xserver and fluxbox?

Boots in 17.5 seconds here :)

Please send your computer to me so that I can test and review it. :-)

---

### Post by Ck.asdf on 2008-09-16
[quote]OO.org isn't a text editor[/code]
I know it's not a text editor, but I figured I'd add that for whatever reason.  I've edited my post.

When I get some time, I'll check out minix & debian base, to see what they offer.  Thanks for the suggestions!

How are those two as far as wireless drivers?  As a note, ubuntu recognizes my wireless card with no problems.

---

### Post by Vivaldi Gloria on 2008-09-16
> **Ck.asdf said:**
> How are those two as far as wireless drivers?  As a note, ubuntu recognizes my wireless card with no problems.

They have the same drivers with their full CD versions. Check CLI in my sig to read about cli versions of ubuntu.

---

### Post by Ck.asdf on 2008-09-16
I read the CLI stuff, and that sounds nifty!
If I were to install:
(2) Minimal CD available from MinimalCD

Approximately how fast do you think that would boot up, in comparison to a regular Ubuntu installation?

Thanks for the info!

---

### Post by Vivaldi Gloria on 2008-09-17
> **Ck.asdf said:**
> I read the CLI stuff, and that sounds nifty!
If I were to install:
(2) Minimal CD available from MinimalCD

Approximately how fast do you think that would boot up, in comparison to a regular Ubuntu installation?

Thanks for the info!

Well, you heard the man say 17.5 seconds! This is with a very light desktop - fluxbox. No desktop - even faster! 

With the full ubuntu gnome desktop it takes about a minute. Actually, one of the planned feautures for ubuntu 9.04 is to make the boot quicker.

---

