---
title: "Help for installing Windows, I only have ubuntu"
date: 2008-09-15
forum: General Help
---

### Post by monchito on 2008-09-15
Ok, I am completely desperate now.
I bought a Acer Aspire 5930, in July, it had Windows Vista, I decided to install ubuntu,but I am a newbie, so when i installed it, i let the installation cd do the partitions automatically, to my surprise I think it deleted the windows partition...so i only have ubuntu 8.04 now, which i like but i really need to get my windows back aswell.
i dont have the boot cd, since i didnt do the recommended safety copy they suggest at the beggining...but my vista is legal since i have the code and everything under my laptop...
i have a copy (not very legal) of windows xp, and i tried to boot it...the booting program launches, and starts detecting hardware and stuff...but a moment comes when the screen goes blue and says it has some problems with memory and stuff, so i cant install that either...
So my first question is, if i burn a vista dvd, then use my serial number, should it work? 
I really need windows for the moment because my wifi doesnt have a stable solution yet intel wifi link 5100/5300...and i need wifi...
Im also having problems making a pptp tunnel, its way too complicated for my level of linux...and i really need it to access an ethernet internet connection in my uni. 
So basically i want to delete ubuntu, install windows, and then try to install ubuntu on a partition again. But the main thing is to get my windows back.
 How can i do this...i am seriously desperate, i have read a lot of threads, but they dont really give me a solution I understand fully...anyone out there patient enoguh for helping me????

---

### Post by whizbaby on 2008-09-15
> **monchito said:**
> 
So my first question is, if i burn a vista dvd, then use my serial number, should it work?
Perhaps, but the act of burning is certainly illegal and it might not work, too. You could purchase a cheap (linux supported, around 15€ in my area) USB wifi device and get a connection with that. Then install virtualbox (a virtualisation software) and install XP on a virtual machine, so you can start that if needed(sounds complicated - but is a piece of cake, really).
Having no vista installation CD all you can do is write a letter to M$ support and try to get a CD from them with your product key under the laptop, but I doubt that it'll be for free...

---

### Post by shaggy999 on 2008-09-15
Copyright law allows you to make one backup copy of a CD, so I don't see how burning a copy of Vista is illegal if you already own a copy. If what you're saying is that you have Vista, but you don't have the install DVD (which is what I think you're saying) and you're asking if it's legal to download a copy of Vista and use your key, well.... if you want legal advice, go find and pay a lawyer.

I certainly don't advocate downloading Vista, even if you do have a key, and besides, from what it sounds like your system probably had an OEM key, which means you'd need the OEM version of Vista anyway instead of Retail.

My suggestion is that since you bought this machine from Acer you call them up and ask how to re-install windows (don't mention anything about ubuntu because they won't help you if you have non-sanctioned OS installed). Just tell them your hard drive got hosed and you need to re-install Vista. My guess is that since it didn't come with a CD they'll probably "sell" you the OEM CD for like an extra $50 or something.

---

### Post by whizbaby on 2008-09-15
> **shaggy999 said:**
> Copyright law allows you to make one backup copy of a CD, so I don't see how burning a copy of Vista is illegal if you already own a copy.
I guess its different from country to country. Here its illegal to copy it unless allowed explicitely by microsoft, and I cant see anything about the right to have a copy in their license agreement.
> 
My guess is that since it didn't come with a CD they'll probably "sell" you the OEM CD for like an extra $50 or something.
See you can get 3 wifi devices for that money.

---

### Post by wobbiebobbie on 2008-09-15
I agree with shaggy999 call acer. If you dont have to restore CD and you let  ubuntu use the (entire disk space)  then you hosed your partition that contains your  VISTA O/S  if you did something different you might have a chance.   you need to remember the steps you took to set up ubuntu. I dont Know

---

### Post by pbotros1234 on 2008-09-15
Do
```
sudo fdisk -l
```
And report what you get

---

### Post by shaggy999 on 2008-09-15
> **whizbaby said:**
> I guess its different from country to country. Here its illegal to copy it unless allowed explicitely by microsoft, and I cant see anything about the right to have a copy in their license agreement.

See you can get 3 wifi devices for that money.

Yes, but you don't get Vista, which is what he expressly stated what he wants.

---

### Post by monchito on 2008-09-16
yeh, for sure, im not going to buy a wifi usb!  apparently in the next release of ubuntu it should be working my intel wifi link 5100/5300, but thank you anyway

---

### Post by monchito on 2008-09-16
Ok, I have to say, I already called acer,2 months ago, told them stupidly I deleted windows vista while installing ubuntu, and they basically told had to by me I had to buy a 60 euro restore CD, following a very tedious and long process. At the moment I am not even in my home country, so that option is complicated...
When I installed ubuntu I let ubuntu do the partitioning job...yes of the full disk(stupid of me I know)
What is an OEM key...?
Finally...does anyone know about pptp... because I have a domain a password and a username to access the internet in my dorm at uni...what do i have to type to access the internet with that information
(Even thought this seems a different topic, it is basically the reason why i need windows, the pptp is easy and straight forward, and my wifi card actually works)
Thank you to all but my problem is not about legal stuff, im asking for a solution please!

---

### Post by shaggy999 on 2008-09-16
Microsoft provides a slightly altered version of Windows to manufacturers (Dell, Lenovo, Acer, Toshiba, HP, etc) than it sells in stand-alone copies at stores (like Best Buy or Circuit City). The manufacturers are referred to as "OEMs" or "Original Equipment Manufacturer's". So the versions of windows given to these oems are called Windows OEM whereas the version of Windows at the store is "Windows Retail". This menas there's a "Vista Ultimate Retail" and "Vista Ultimate OEM". Likewise, the codes that are sent out are associated with either an OEM or Retail version. So if you try to use an OEM key with a Retail version of Vista or a Retail key with an OEM version of Vista it won't work.

Since you have a machine from Acer, and Acer is an OEM, then that means the key that you have is an OEM key. So you need an OEM install disk. The "restore cd" that Acer tried to sell you for 60 euros is that OEM disk (well, actually... nevermind, it gets complicated). Short story is you need an OEM install disk to use that key which means you have to ask Acer for it, which means you gotta drop 60 euros.

Or just go to Best Buy and pick up a brand new Retail copy of Vista, which will come with a Retail key along with it.

---

### Post by monchito on 2008-09-17
thank you shaggy, nice bit of info!! still no better solution! oh dear

---

### Post by whizbaby on 2008-09-17
Perhaps theres something you can try with the winxp cd. Theres two things you need to do:
1) insert a live cd and delete the linux partitions, then make a partition for windows (not necessarily the entire disk as you might want to install ubuntu :)) and format it with filesystem ntfs.
2) start the windowscd and hit F5 on the blue screen while its searching for devices (just keep hitting F5 until the screen changes). There you can select computer types to install to. Choose your type and give it a try.

---

### Post by shaggy999 on 2008-09-17
You're kind of SOL without a windows installation CD. Basically from what you've told me all that you have is an OEM key. I don't know anything about pptp but you mentioned wireless problems -- have you tried using ndiswrapper w/ the windows drivers for your wirless card? That would at least get you wireless in ubuntu, which isn't what you're asking for, but things would probably be better if you at least had your wireless working.

---

### Post by yarn on 2008-09-17
I am not sure if this helps but i know that some new laptops come with a extra partition with the recover for windows on it. There are certain keys that you hit while windows is booting and it automatically starts the restore. Only problem is I dont know if the ubuntu deleted that also...to my understanding was that you couldnt delete that partition...does anybody know what i am talking about?  sorry if that doesnt help much.

---

### Post by SPr on 2008-09-17
> **yarn said:**
> I am not sure if this helps but i know that some new laptops come with a extra partition with the recover for windows on it. There are certain keys that you hit while windows is booting and it automatically starts the restore. Only problem is I dont know if the ubuntu deleted that also...to my understanding was that you couldnt delete that partition...does anybody know what i am talking about?  sorry if that doesnt help much.

[http://ubuntuforums.org/showpost.php?p=5796909&postcount=6](http://ubuntuforums.org/showpost.php?p=5796909&postcount=6)

Follow pbotros1234's advice in the sixth post in this thread.

---

### Post by whizbaby on 2008-09-17
@shaggy
no, I believe he said hes got an XP cd
@yarn
on most laptops I've seen theres only the special hardware drivers and some repairing software. I doubt you can get a whole system out of there, but it would indeed come in handy if one tries to install windows on the laptop (mainboard,graphics,network,sound, touchpad and evtl bluetooth and usb drivers)
But I'm quite sure you can delete that partition,too, because I already did rather often^^
If you tell ubuntu to wipe the whole drive then it will.

---

