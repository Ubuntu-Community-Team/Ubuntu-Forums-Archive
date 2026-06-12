---
title: "Guys please help me! I cannot hear any sound when installing ubuntu 10.4  n my laptap"
date: 2010-09-05
forum: Hardware
---

### Post by ansary on 2010-09-05
I installed ubuntu 10.4 at my laptap yester day and i noticed that i cannot hear any sound..
I try also any possible answers but it didnt work!

The Brand of my laptap is ACER and i have intel-hda built-in but when i try to enter a command lshw in the terminal ,it appears that my MULTIMEDIA is UNCLAIMED.. so im sure that this is a good hint for u guys to help me to fix this..

---

### Post by 73ckn797 on 2010-09-05
Is there a speaker icon on the top panel? click on it and see is the volume is turned down.

---

### Post by ansary on 2010-09-05
I have full volume right now..

i also set my volume at 100% in sound preferences.. and i cannot hear no sound at all

---

### Post by ansary on 2010-09-05
Guys please Help me..

Im still stranded!

---

### Post by 73ckn797 on 2010-09-05
Repost under Multimedia and Video. Re-title as No Sound. There are many threads that deal with this issue.

Look here: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by ansary on 2010-09-07
guys when i try to enter dis command "sudo aplay -l".. it says that i have no sound card!


what the heck is happening??

i used my laptap in 5 months in windows but everything is fine..

guys help me plz.. im really a newbie in ubuntu..

---

### Post by s0rc3r3r on 2010-09-07
I am pretty new to Ubuntu Myself
But..I think I can give you some pointers to what your problem must be

1) You should have the proper sound driver installed for your sound card. Else the Ubuntu wont be able to do anything with the hardware.

DO check the threads which has issues discussing your laptop model.

2)To play the normal music and video formats you should install the 'Restricted Packages',.That means even if you have your sound drivers installed,m you must have the restricted codecs to play the music or video.

YOu can get details on restricted formats here:[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)


Well!! WIth UBUNTU my friend, there is always a way out!!
It's just a matter of looking!

If you could post in the system specifications here,m that would be a good start for people who would like to help you with a solution.

---

### Post by ansary on 2010-09-07
I already found what my problem really is ..

i got no sound card detected bcoz i need some drivers for my sound card that good for linux, but somehow i dont know where i can find those stuffs..i tried to google it but i didnt find any.. IF u have some any known links for some drivers pls post it here in my thread..

i used intel-HDA and its not detected in my ubuntu laptap!

i use aspire 4745G..

Sorry for my untalented to find those stuffs..

---

### Post by community nerd on 2010-09-07
yeah, i have the same problem on my hp notebook

---

### Post by ansary on 2010-09-08
guys im still stuck..

---

### Post by croivzeba on 2010-09-08
What would have really helped was if you provided your system specifications but it's all good I did some googling ;).

I have an hp laptop and just like me you need the new realtek sound card drivers off their site.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

Scroll down to linux and download them.

Copy the downloaded file to your desktop so you can just copy and paste the following into your terminal.

Open terminal

cd Desktop
tar xvjf LinuxPkg_5.15rc10.tar.bz2
cd realtek-linux-audiopack-5.15/
tar xvjf alsa-driver-1.0.23-5.15rc10.tar.bz2 
cd alsa-driver-1.0.23/
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install

Reboot your system and it should work... I added a couple of unnecessary sudos but oo well who cares..

If you got any errors post them here. If you get an error saying it couldn't patch a file you need to install patch from the synaptic package manager.

---

