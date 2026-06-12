---
title: "Wireless card causes laptop to hang on boot"
date: 2006-02-17
forum: Hardware &amp; Laptops
---

### Post by kenailes on 2006-02-17
i have a linksys wireless card and used the wireless configuration tool I downloaded using autoget.  the wireless card works for when i get things up and running, but when i boot, if the card is plugged in, the laptop hangs at the bootup.  i have to remove the card, boot the laptop, log in, the plug the card back in and manaully activate the card.

Is this God intended it to be done or am I missing something?

---

### Post by mazlusus on 2006-02-23
I had a similar problem with mine and somewhat accidently I hit the 'Print Screen' button and it loaded the next item and then stopped, I pressed Print Screen again and then it worked fine. If I boot my computer with my wireless switch turned on it does this...kind of strange but hope it helps you out.

---

### Post by K.Mandla on 2006-02-23
Does CTRL+C do anything for you? My machines have hung once or twice on boot because the router was preoccupied or the modem was restarting, and that dropped them out of whatever wait state they were in. Don't know if it will help, but it might accelerate the process for you.

---

### Post by Crayoneater on 2006-02-23
yea, ctrl+c will skip whatever step it is currently on....you could change the interfaces so that the wireless card isn't auto(go to /etc/network)....then you could use a program like gtkwifi or something and then it will setup you wireless connection for you....or something like that....i think that might make it not hang on boot....or you could try to install initng which will make your computer boot up faster and it might keep it from hanging on boot, there are some good tutorials on how to setup initng on these forums...

---

### Post by barryjj on 2007-10-26
I have this same problem.  It only started after I upgraded to 7.10 (I was running 7.04).

I have a linksys wireless B PCMCIA card -- if I remove it, boot, and plug back in once the welcome screen shows up, I can do an ifdown and ifup for wlan0 to make everything work alright.

However, if I leave the card in, the progress bar gets to about the 98% mark (just a sliver remains) and the capslock and scrolllock lights flash in sync at a regular interval.

I followed the same setup for using the windows wireless drivers as I did last time, the guide found in the WifiDocs under the help community (granted, these were for 7.04).  Something must've  changed to make this happen in the new release -- anyone have a clue on how to solve it?

For the record, ctrl-C does NOTHING... once it enters this state with the startup progress bar mostly filled and the two lights start blinking in sync, I'm done for... it doesn't respond, I have to hard reset and remove the card if I have any hope of it booting.

(I also have a problem trying to get my damn nVidia card to use the restricted drivers, but my first goal is making wireless work consistently and without it being a chore.)

Any help is appreciated.

Thanks.

---

