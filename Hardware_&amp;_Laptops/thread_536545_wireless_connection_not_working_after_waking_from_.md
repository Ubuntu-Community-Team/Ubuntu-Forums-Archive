---
title: "wireless connection not working after waking from hibernation"
date: 2007-08-27
forum: Hardware &amp; Laptops
---

### Post by Green_Star on 2007-08-27
My wireless card is Netgear Wg511 V2, i installed ndiswrapper to use this card. It works fine when i  do a fresh boot, but will not work after waking up from hibernation. to make it work i just uncheck the 'Wireless connection' from the Network Settings window, wait till it complete that operation and again check the 'Wireless connection' check box. after this process my wireless connection works fine. Is there any way I can automate this, like when ever i wakeup from hibernation this operation should run automatically, so I do not have to do manually. 

Thanks in advance.

---

### Post by Green_Star on 2007-08-30
any help?

---

### Post by bjarneh on 2007-08-30
1. look for scripts that are executed when your machine wakes up (shuts down) 
(ask here on the forum perhaps, something must know)

2. try to find your command-line equivalent to your key-pressing scheme


then combine these two things in your very own script, and run that whenever your computer wakes up, that should do it. but it does look like you will have to fiddle around a bit, which might the reason for nobody giving you a straight answer (quickly) here at the forum :-)

---

### Post by EXCiD3 on 2007-08-30
Many people have been experiencing the same problem as you. Unfortunately Feisty does not seem to have that great of laptop support. Gutsy is claimed to have fixed my issues relating to laptops, but isn't due out until October, unless you want to use a testing release of it. For now you can try this: > **Suspend/Hibernate**
 Supposedly adding "nosmp" as a boot option, disabling Sync To Vblank in Beryl, and if you edit the /etc/default/acpi-support and set POST_VIDEO=false, suspend and hibernate
        should work better.That is taken from my HP laptop Howto that I wrote, but not all of that may pertain to you. If you aren't using beryl, compiz or compiz fusion, skip the sync to vblank part. Try it out and see if it works better for you. I still had some issues resuming but most of them were fixed after using this boot option.

Just add it as a boot parameter for you kernel and you should be good to go.

---

### Post by Green_Star on 2007-08-31
Thanks Ex, could you please give me more details like how to do that etc?

I have this problem from very long time, i am keep trying to solve this problem from almost 3 to 4 months, but no luck.

i am attaching a screenshot where i am unchecking and checking the option after wakeup from hibernation.

---

### Post by Green_Star on 2007-09-02
bump

---

