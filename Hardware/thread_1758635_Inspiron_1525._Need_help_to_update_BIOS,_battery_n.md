---
title: "Inspiron 1525. Need help to update BIOS, battery not charging."
date: 2011-05-14
forum: Hardware
---

### Post by Slobs on 2011-05-14
I am running 10.04 on a Dell Inspiron 1525.  I've been having troubles with the battery charging. Or even being recognized for that matter.  It happened two days ago.  If my power cord come unplugged the PC shows a "batter dead" message for a quick half a second then shuts off.  It was suggested I need to update my BIOS but I'm not sure how to do it as the .exe won't open in Wine.

I'm not really tech savvy...  I use Ubuntu because its super fast and easy to use, not because I have any clue about how it all works. So in saying that, I really appreciate any help, but keep in mind I'm fairly tech illiterate.

---

### Post by PhantmKllr on 2011-05-14
I'm not sure if you can update your BIOS from within Ubuntu, especially Wine.

Besides, maybe your battery is actually dead (can no longer hold a charge). How long have you been using your computer, and do you use it a lot unplugged? You may have to consider purchasing a new battery from your computer's manufacturer.

---

### Post by lidex on 2011-05-14
As for bios update:
[http://www.google.com/search?client=ubuntu&channel=fs&q=bios+update+dell+linux&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=bios+update+dell+linux&ie=utf-8&oe=utf-8)

---

### Post by Slobs on 2011-05-14
> **PhantmKllr said:**
> I'm not sure if you can update your BIOS from within Ubuntu, especially Wine.

Besides, maybe your battery is actually dead (can no longer hold a charge). How long have you been using your computer, and do you use it a lot unplugged? You may have to consider purchasing a new battery from your computer's manufacturer.

I always have kept it plugged in.  This is actually the only time I have used it without the charger for more than a few minutes as I'm on the road.  The last time I used it before the battery quit showing up it lasted a little over an hour, so the battery seems to be working.

Something I just thought of that I didn't think would matter, is the charger I'm using is not a dell charger... Its working to keep the laptop on when plugged in, but the batter isn't registering.

---

### Post by BertN45 on 2011-05-14
Maybe the charger has killed your battery by charging too fast. If the battery is dead, work without battery or buy a new battery and an original Dell charger.

My Dell charger for an Inspiron 1521 has as output 19.5 Volt and 3.34 Ampere. If your charger has much different values you have an incompatible charger.

I would not update the BIOS, unless it is a known problem that is mentioned by DELL as a reason to update the BIOS. Besides in the past it worked on battery and that means it is not the BIOS.

---

### Post by lidex on 2011-05-14
> I would not update the BIOS, unless it is a known problem that is mentioned by DELL as a reason to update the BIOS. Besides in the past it worked on battery and that means it is not the BIOS.

I'm pretty sure he stated it's never been off the charger. That in itself can be a problem. 
You need at least a couple of discharge/recharge cycles to properly condition the battery. 
I'm thinking the bios reports the battery status so it may actually help to update.

---

### Post by BertN45 on 2011-05-14
> **lidex said:**
> I'm thinking the bios reports the battery status so it may actually help to update.

I am convinced for 95% that it has nothing to do with the BIOS, since in the past he used it at least once for an hour on battery and a couple of times for a couple of minutes. So everything was OK and working. A BIOS is a PROM program and that does not change or gets defect. If it worked in the past, the BIOS is OK.

Batteries are however very sensitive amongst other for temperature and he used a NON DELL charger and that might have damaged his battery. It is not a joke that all companies say ONLY USE WITH THE ORIGINAL CHARGER.

---

### Post by lidex on 2011-05-14
I disagree but i respect your opinion.

I had issues installing ubuntu on my pc and needed 2 bios updates before I got it to work.
Now all is good and I run 11.04 with no issues.

---

### Post by PhantmKllr on 2011-05-14
As I said, I'll be hard to install BIOS updates within Ubuntu, since manufacturers tend to release them as Windows executables.

---

### Post by BertN45 on 2011-05-15
> **lidex said:**
> I disagree but i respect your opinion.

I had issues installing ubuntu on my pc and needed 2 bios updates before I got it to work.
Now all is good and I run 11.04 with no issues.

I am happy tat the BIOS upgrade helped for you and I know it is somewhat complicated if you do not run windows. 

You have however to realize that there is a difference between an opinion and logical reasoning. In computing we are dealing facts. Finding a bug is a kind of detective work based on facts and the reasoning gives probable and less probable suspects and based on that you look for more evidence.

You installed a new OS with a new 3D user interface and if you have not the latest BIOS, it is wise to upgrade it, if you run into problems. What was right in your case, need not be right in other cases.

This battery problem is different. Everything including the BIOS worked before, so something has been broken during this week. Very probably the OS error report is true and the battery is defect. So normally we first check the battery. A less probable cause could be an update of Ubuntu 10.04 causing the problem.

---

### Post by Slobs on 2011-05-15
Thank you everyone for all the replies.  Updating the BIOS through Ubuntu seems too complicated for me, and as some of you have said is probably not the problem.  I'd buy a new battery, but like I said I almost always use this plugged in, so I'll just continue to do it that way.

Thanks again for all the help!

---

### Post by oscarFrance on 2011-06-04
Hi,

If it's still on time, I recommand you the following link to do a BIOS upgrade from Ubuntu:
[http://muzso.hu/2010/03/29/how-to-put-dos-on-an-usb-drive-using-linux](http://muzso.hu/2010/03/29/how-to-put-dos-on-an-usb-drive-using-linux)

BUT FIRST: backup your harddrive on a external USB harddrive just to get a recovery option of you do any mistake.

So the first step is to dedicate one USB stick to flash it with FreeDOS using the procedure of the link above
Then copy the Dell latest bios firmware (as of today it's the file: 1525_A17.EXE)
on this USB stick.
The reboot your lapto, press F12 during the BIOS boot step, then choose the "USB device"

After you get the dos prompte, just type: 1525_A17.EXE  then press enter.

Feel free to ask me details on the procedure if necessary.
But again, first do a complete backup of your laptop on a external USB disk!

Regards,
Oscar

---

