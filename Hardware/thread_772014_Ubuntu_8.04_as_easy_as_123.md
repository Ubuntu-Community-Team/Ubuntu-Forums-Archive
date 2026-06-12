---
title: "Ubuntu 8.04 as easy as 123"
date: 2008-04-28
forum: Hardware
---

### Post by macca600 on 2008-04-28
My happy experience.


Laptop = ASUS F3Sv    200gig hd  nvidia geforce 8600m GS 256mb
        2 gig Ram.
 	DVD multi burn and lightscribe works
	wifi works
	Card:HDA Intel

        Chip: Realtek ALC660-VD works
	ethernet working
        Bluetooth working
        FN function butons work

current resoultion 1680x1050 50 hz

Laptop fan runs as normal ,when playing SteamGames runs a bit.


1-To get sound working all I did was add this to bottom of alsa-base in /etc/modprobe.d/
 options snd-hda-intel model=lenovo
 then ran alsamixer in console ,dropped volume on inbuilt mic to cut ou feedback etc.

2-Installed envyNG  a usefull tool for downloading ati and Nvidia drivers for you system and installing it.
 Ran it, got the latest drivers installed with no problems.

3-apt-get install wine  I want to play Steam games :)

Just a quick rant abount how cool this edition is , I currently have dreamlinux and mandriver power pack installed too.

a) my volume buttons work,actually all my function keys do .

b) Im on Telstra BigPond 3G network ,installed Kppp ,3g modem Sierra Wireless AirCard 880E 7.2mb was detected and attached to USB0,1,2,3
   nomally i have to modprobe usbserial vendor=0x1199 product=0x6852, but not this time , added AT+CGDCONT=1,"IP","TELSTRA.BIGPOND"
   to custom strings 2 ,and then off I go surfing the net and playing games ,get good speeds.

c) Customized theme , look and feel etc.


Steam Counterstrike-Source runs a treat under wine , I can play full screen and get 70-100fps no problems on dxlevel 80, did run on dxlevel90 but seems
to drop a few frames either way it looks a treat . Sound on it works fine, left as default alsa. added steam.exe to application tab to allow steam frieds chat.
Only problem is if you join Internode Australian servers there Motd crashes css, something to do with html rendering so after steam loads,I change gecko in regedit,add extra value
then change back when finished. It is a documented problem for some users, go figure.
Window mode is good too at 1300x800 lol. The games seems to run faster on linux, well thats my opinion.

All up everythings running sweet. 
ps I do have 64bit installed too,but like 32 bit.
I use aptoncd to back up my packages.
I have used pretty much every flavour of linux this one remains to be one of my favourites for everyday use So What MOre Do U WANT!!!

---

### Post by morticae on 2008-07-16
Just a note to say that this DOES work for whatever reason.
I set up a lot of laptops for business purposes so I don't have a lot of time to tinker, but this one intrigues me.  My guess is there is something non-standard about lenovo's intel soundcard hardware that ASUS happens to share?  That or K-waves.

The laptop I'm working on is an ASUS F3SV-B3 with Hardy 8.04 installed.

---

