---
title: "Suspend does not work when closing lid.  TX2"
date: 2009-11-20
forum: Hardware
---

### Post by Digikid on 2009-11-20
Greetings all.

After many many reinstalls I FINALLY got Ubuntu working the way that it should be working....or so I thought.

Now the suspend does not work.  I close the lid....the WLAN light goes orange and then goes back to blue.  It should stay orange.  The monitor does not shut completely off and the power light stays steady instead of pulsing as it should.

Fully updated on everything ( drivers, BIOS, Prop drivers ) and the power settings are as they should be.

SO tell me....what can I do to fix this?

---

### Post by sfordin on 2009-11-20
Do you have an SD card or suchlike mounted in a card reader slot on your machine? I found that hibernate/suspend does not work on my Toshiba A205 laptop unless I first eject the SD card I keep mounted in the card reader slot. See [http://ubuntuforums.org/showthread.php?t=1330953]("http://ubuntuforums.org/showthread.php?t=1330953") for more information.

Scott

---

### Post by IcarusR on 2009-11-20
Is it set to suspend when the lid is closed ?
System > Preferences > Power Management

---

### Post by Digikid on 2009-11-20
> **sfordin said:**
> Do you have an SD card or suchlike mounted in a card reader slot on your machine? I found that hibernate/suspend does not work on my Toshiba A205 laptop unless I first eject the SD card I keep mounted in the card reader slot. See [http://ubuntuforums.org/showthread.php?t=1330953](http://ubuntuforums.org/showthread.php?t=1330953) for more information.

Scott

I found this as well and tried it.  No luck.

> **IcarusR said:**
> Is it set to suspend when the lid is closed ?
System > Preferences > Power Management

As stated above in my previous post yes I did check the power settings and they are as they should be.

---

### Post by IcarusR on 2009-11-20
> As stated above in my previous post yes I did check the power settings and they are as they should be. 

Sorry my fault, didn't read properly.

---

### Post by Digikid on 2009-11-20
Not a problem.  ;)

We all make mistakes.  :D

---

### Post by confused_user on 2009-12-04
same problem here but it's hibernate for me.  I close the lid and the damn thing stays on until the battery runs out.  It has worked previously but seems to have stopped now.

another major problem going answered?

---

### Post by border on 2009-12-09
Does suspend (and hibernation) work at all?
I mean if you just try it (in the power off menu)...
On my TX2 neither of them works

If anyone can point me at any logs which should be able to clear things up I would be glad to be of any help. But as it is I have no clue

cheers

---

### Post by Digikid on 2009-12-10
I just ended up reformatting.

---

### Post by border on 2009-12-10
So if I understand correctly you reinstalled ubuntu and it just works???
seems quite odd to me but if it works I´m willing to try it :)

---

### Post by border on 2009-12-14
maybe my problem is because of compiz being enabled and so using the binary only ati catalyst driver?
I seem to encounter other problems to because of it (crashing audio programs like mixx and zynaddsubfx in combination with jackd).

---

### Post by confused_user on 2009-12-20
> The problem is related to a massive refactoring of gnome-power-manager, which now uses the devicekit-power daemon instead of the recently deprecated hal. Particularly, the problem has to do with the inability of devkit to determine whether we're on AC or battery reliably.

> sudo add-apt-repository ppa:jmartinj/dkp
sudo apt-get update
sudo apt-get upgrade

[http://potrerohacaido.blogspot.com/2009/11/ubuntu-910-doesnt-suspend-when-closing.html](http://potrerohacaido.blogspot.com/2009/11/ubuntu-910-doesnt-suspend-when-closing.html)

[https://bugs.launchpad.net/ubuntu/+source/devicekit-power/+bug/384304/comments/29](https://bugs.launchpad.net/ubuntu/+source/devicekit-power/+bug/384304/comments/29)


works for me :)

---

### Post by border on 2010-01-14
Does not work for me.
Problem is that it does not want to suspend nor does it want to hibernate. Even if I try it manually.
Any thoughts on how to debug that?

---

### Post by digitalchemystery on 2010-03-20
My computer stopped being able to sleep after I followed one of the steps for getting sound to work by creating the file /etc/pm/sleep.d/fixsound with contents "alsa force-reload". After I removed this file, it worked again.

If you've done as I did, that might help.

---

