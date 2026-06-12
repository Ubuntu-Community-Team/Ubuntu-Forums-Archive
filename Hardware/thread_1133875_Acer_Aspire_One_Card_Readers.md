---
title: "Acer Aspire One Card Readers"
date: 2009-04-23
forum: Hardware
---

### Post by teh603 on 2009-04-23
So I tried the AAO card readers in Jaunty, and found that the left one is hotpluggable "out of the box," while the right one is still not hot pluggable unless a card is installed at boot time.

Has anyone got a workaround to make both work without having a card sticking a quarter inch out of the right reader at boot time?

---

### Post by meeples on 2009-04-23
i have an acer aspire one also, i'd love it if both readers would work they way they should!!](*,)

---

### Post by teh603 on 2009-04-23
Bumping. Anyone got the workaround?

---

### Post by teh603 on 2009-04-24
Bumping again. Anyone?

---

### Post by himura on 2009-04-25
> **teh603 said:**
> So I tried the AAO card readers in Jaunty, and found that the left one is hotpluggable "out of the box," while the right one is still not hot pluggable unless a card is installed at boot time.

Has anyone got a workaround to make both work without having a card sticking a quarter inch out of the right reader at boot time?

Maybe I'm missing something here, but since few days ago I have run UNR on a AAO (160 HD, 1G RAM) and both card readers are working pretty well (especially the multi-card one), I mean, I don't need to reboot in order to mount the Sd card. Saluti.

---

### Post by teh603 on 2009-04-25
I'm not using UNR, and flat-out refuse to us any OS on it that would make people say "Oh, what a nice overgrown PDA you've got there. How much did you overpay for it?"

I'll try again, but I'm pretty sure its not working in desktop edition.

---

### Post by crossy on 2009-04-26
Hi '603 - yes I just got rid of Linpus on my AAO and sure enough neither card readers are working for me either - so it's _not_ just you! :confused:

That said, my WLAN light also doesn't work - and I'm sure that was one of the "big ticket items" that was supposed to work with Jacky.

> I'm not using UNR, and flat-out refuse to us any OS on it that would make people say "Oh, what a nice overgrown PDA you've got there. How much did you overpay for it?"

Now I think you're being pretty unkind here - the UNR version is actually pretty good, and far from looking PDA-like, I actually think it looks pretty stylish, (*sheesh guys, why does it always have to be brown!*)

bob

---

### Post by V-600 on 2009-04-28
I've just installed UNR 9.04 on my aspire one (8GB SSD, 512 MB memory). At present neither of my card readers are seeing a 16GB sdhc card whether its present at boot up or not.

Also as with the post above, my wireless light is not working either (though that's not really a big deal to me).

---

### Post by londonali1010 on 2009-04-28
Just to concur with V-600, I have the same problem.  I have an Acer Aspire One with 8GB SSD, 512MB RAM and I upgraded from 8.10...Neither card readers work for me!  I will probably have a look through the 8.10 installation guide and see if I can tweak it the same way...Worth a try?

---

### Post by V-600 on 2009-04-28
I guess so. I have also read that you need the most recent bios for things to work properly. Mine is already the most recent (I guess if your aspire one is only a few months old yours will be too) but its worth checking.

---

### Post by teh603 on 2009-04-28
> **V-600 said:**
> I guess so. I have also read that you need the most recent bios for things to work properly. Mine is already the most recent (I guess if your aspire one is only a few months old yours will be too) but its worth checking.

That's a slight problem. Mine's a display model from the local Best Buy. I don't think the BIOS was ever flashed, because it also has the issue with gnome power manager freaking out in Intrepid.

I'm also a little reluctant to just take it in to service and have them flash it. They might not do anything thinking I wouldn't know the difference, but still charge me an arm and a leg.

---

### Post by snakeman21 on 2009-05-06
> **teh603 said:**
> That's a slight problem. Mine's a display model from the local Best Buy. I don't think the BIOS was ever flashed, because it also has the issue with gnome power manager freaking out in Intrepid.

I'm also a little reluctant to just take it in to service and have them flash it. They might not do anything thinking I wouldn't know the difference, but still charge me an arm and a leg.

I have the files that you need to flash the bios.  If you want them, just let me know.  It's very simple, just two files that you put on a usb stick.  You put the stick in the acer when it's off, and hold FN and ESC while you power it on.  Then wait until the power indicator stops blinking, shut the lappy off, and turn it back on.  Bingo, flashed bios.  If you want me to send you the files, email me [email]snakeman_21@yahoo.com[/email] 

Also, I am having the same card reader issue.  Left one works fine, just as it should, hot-pluggable, out-of-the-box.  Right one has NO funcionality, not even if I boot with a card inserted.  I had the same problem with Intrepid, and was hoping that the Jaunty NBR would have a patch... Guess not though:(

---

### Post by teh603 on 2009-05-06
Honestly, the power manager issue doesn't seem to exist in Jaunty, or someone patched X.org to deal with it. Probably the latter.

---

### Post by stchman on 2009-05-06
> **teh603 said:**
> So I tried the AAO card readers in Jaunty, and found that the left one is hotpluggable "out of the box," while the right one is still not hot pluggable unless a card is installed at boot time.

Has anyone got a workaround to make both work without having a card sticking a quarter inch out of the right reader at boot time?

Neither of mine are hot pluggable.  If you populate each SD card slot at bootup they are then hot pluggable.

I wish they would get pciehp working for Jaunty.

---

### Post by teh603 on 2009-05-07
One of the reports I read said its a BIOS issue that can only be patched by flashing, while others say that flashing the BIOS won't make a difference. To be honest, I'm going to leave my BIOS alone. I've heard too many horror stories of people bricking their eeePCs because the Xandros Software Updater corrupted the file on download, or something like that.

---

