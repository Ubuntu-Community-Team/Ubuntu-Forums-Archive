---
title: "How would I configure sound card"
date: 2008-11-08
forum: Hardware
---

### Post by Lakeside on 2008-11-08
I usually post in the `Absolute Beginner Talk` section (can move this if you want). I jsut installed Hardy Heron server (8.04) and don`t have any sound on any movies I try to play (even after downloading/installing suggested codecs etc) because I did not configure my sound card (have googled, but don`t know how to do it, and I forget even what sound card I have. Any help would be appreciated.  I want Hardy Heron, mainly to learn serving, and a little web design, but the kids are getting mad lol
*edit* Finally got the bright idea to search here: [http://ubuntuforums.org/showthread.php?t=205449&highlight=configure+sound+card](http://ubuntuforums.org/showthread.php?t=205449&highlight=configure+sound+card)
:( edit again*  I tried to follow this advice: Check to see if the ALSA driver for your sound card exists. Go to [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) and search for your sound card (chipset) manufacturer in the dropdown box. You'll be given a matrix of the sound cards made by the manufacturer. Try to match the chipset you found in step 2 with the driver(green hyperlink text)....but I don`t think the link went to the sight he used, I couln`t make sense out of it anyways lol. So, if anyone knows how I can do that step (finding my sound card`s `chipset`??) I would really really appreciate some help. thanks in advance :)
*warning*  Ok, this may only be a situation unique to me but..I am currently tying this on another comuter (great, now Im missing  a few keys  is a black screen, with writing resembling the terminal, where I would have to enter a command to re-enter I assume (no gui or deskto  login! This occurred after re-booting after entering the commands in above guide (to un-install and re-install the sound card drivers I think- but it also warned that that could occur! So...be careful (

---

### Post by Lakeside on 2008-11-10
I still have no sound, and although the guide I mentioned is great ( I learned a few more useful commands) I may need a little help here. It seems my audio sound card (from what I see after `lspci -v) is a VIA audio controller? But I searched the web for an ALSA driver for this card, and just get confused. (hey, it`s been a scary weekend, I had to recover my GUI from the command line..and I`m a NOOB:confused:...but I had great help here!) Would just like to find this driver, and the code to install it, thanks in advance

---

### Post by webbie180 on 2008-11-10
just installed the new Ubuntu 8.10 and I have no sound.I have fixed this problem by installing following commands.



sudo killall pulseaudio

sudo alsa force-reload

and then go to System>Preferences>Sound and change everything to ALSA

---

### Post by Lakeside5 on 2008-11-10
Thanks Webbie180, the first command was ok, but I guess I don`t have alsa on here, as this command:  sudo alsa force-reload  gave me `Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).` So, I must do some sort of `apt-get alsa drivers` or something ? Thanks for explaining this :)

---

