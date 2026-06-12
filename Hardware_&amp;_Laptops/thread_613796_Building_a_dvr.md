---
title: "Building a dvr"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by djrobthaman on 2007-11-15
Hi,

I recently got digital cable and thought to myself, "Wouldn't a dvr be great."  So  I decided instead of buying a tivo box (which requires a subscription to use the damn thing... what the hell!!???) or another ready made dvr, why not get some parts, put it together and make a dvr/dvd player that looks cool and doesn't cost that much and is based on ubuntu.

So, I went to newegg and rounded up some possible culprits for the hardware.  [Here's my list]("https://secure.newegg.com/NewVersion/Wishlist/PublicWishDetail.asp?WishListNumber=6352251&WishListTitle=DVR").  So far it still costs over $300 though :( 

So, I've got some questions and they go something like this...

**SOFTWARE**
I figure I'll be installing ubuntu, vlc and mythTV.  

MythTV will load on startup.
Does anyone know if the remote that comes with the TV tuner works well with mythTV and all its functionalities?
Does the video card I have chosen work well with MythTV?
I think newegg says that there is an RCA video output on the actual video card.  This is why it is on the list.  I want this to work like a regular dvr in that I can connect it to my tv (a big old philips CRT) without any sort of conversion going on inbetween.  Does this RCA output work well with ubuntu?  Is it easily configurable?  Will it give me as good a quality TV picture as my regular dvd player hooked up to my tv?

VLC will load once a dvd is detected.
Will I  be able to use the remote that comes with the TV tuner card to control vlc?
If not, can mythTV play dvds well and will the remote work for that?

Should I instead use a derivative like mythbuntu or is there something else I've never heard of that would better suit my needs?

I don't want to have to hook up a keyboard once I've done the initial software install either.  So is there a way to bypass the login screen automatically so that everytime it starts up I don't have to enter a username and password?

**HARDWARE**
Is all of this hardware compatible with linux?
If anything isn't compatible, what would you suggest as a replacement?
Is there any better hardware I could get instead of what's on that list that won't murder my wallet?

Thanks for all the info,
Douglas

---

### Post by Nem1976 on 2007-11-15
Have you looked at Linux MCE?  I'm in the process of doing the same thing but for multiple rooms and the MCE is the best option I have run across so far.

[http://linuxmce.com/](http://linuxmce.com/)

---

### Post by djrobthaman on 2007-11-15
Nem, linuxMCE looks interesting.  But I notice it seems to suggest that encrypted dvds are not supported.  Do you know if this can be fixed by adding an extra decoder, eg libdvdcss2?

---

### Post by djrobthaman on 2007-11-15
Hmmm... [Check out this remote.]("http://www.ipcrepublic.com/iMon-Remote-3.5-BLACK-Plate-External-Bay-USB-IR-Receiver-iMon-Pad-Remote-Black-Internal-3.5-Bay-_1800_853.html")  I think I just added $100 to my price

The inux mce wiki says it's compatible.  And this thing looks slick.

BTW, anybody know of anything other than mce that might let me play/pause/record digital cable and watch dvds.  While I'm at it, why not something that can index my media over the network and watch all my media files :)

---

### Post by Fire_Chief on 2007-11-15
I noticed a few things missing on your wish list (I'm building a MythTV DVR so I've just been through some of your same questions).

First, you don't have a video out card. The PVR-150 will handle the video capture from your source (cable, sat, etc) but you have to have a card to output the video to your TV. The PVR-150 doesn't do the video output. I'd suggest a low-end Nvidia card with S-video output (if your TV has S-Video input). You may want to get a fanless card to help keep the noise down.

The PVR-150 card you have listed on your wish list does not include a remote.

Since you have Digital Cable, do you have an external cable box that is used to change channels and decode/manage the signal from the cable company? If so, you'll need to look into an IR Blaster to allow Myth (or whatever) to change the channel on the cable box when you tell your DVR to change channel.

Mythbuntu is extremely easy to setup. Knoppmyth is also fairly easy. I've not worked with LinuxMCE. Have tried Geexbox and found it works fine for playing media over the network but not for DVR stuff. I've also attempted a manual build of MythTV on top of Feisty Alternate CD install. This is definitely the hard road but in my case necessary since some of my hardware was not already configured/supported by the all-in-one distros.

---

### Post by djrobthaman on 2007-11-15
By George, I think you're right Fire Chief.  I could have sworn when I made this list newegg said it shipped with a remote.  Well, no bother.  I found one I looks nice [here]("http://www.ipcrepublic.com/iMon-Remote-3.5-BLACK-Plate-External-Bay-USB-IR-Receiver-iMon-Pad-Remote-Black-Internal-3.5-Bay-_1800_853.html").  Based on your research do you know if this is compatible with mythTV???? 

Also, I swear I had a video card in there.  It seems that newegg must have "forgotten" it when I hit the save button.  [Here it is.]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814121542R").  Hopefully this time when I update the list it'll be there. 

But, as you can see, it has an RCA output.  Which is why I had those couple of questions as to whether it made sense to include it in my wishlist.  But, again, what do you think?  I'm really in unchartered territory here when it comes to setting up something like this.

PS, thanks for the suggestion about the IR Blaster.  I probly will need something like that because, as you said, I do have an external cable box.

---

### Post by djrobthaman on 2007-11-15
BTW, are there any IR Blasters that you would recommend?

---

### Post by Fire_Chief on 2007-11-15
Your video card looks like it may work...see here for more info related to MythTV [http://mythtv.org/wiki/index.php/TV_Out]("http://mythtv.org/wiki/index.php/TV_Out")

Same with the iMon remote... [http://mythtv.org/wiki/index.php/Imon#iMON_PAD_Remote_Control]("http://mythtv.org/wiki/index.php/Imon#iMON_PAD_Remote_Control")

Have a look here for some IR Blaster ideas [http://mythtv.org/wiki/index.php/Cottage_IR_Transceivers]("http://mythtv.org/wiki/index.php/Cottage_IR_Transceivers")

---

### Post by newlinux on 2007-11-15
If you have one of the popular motorola boxes you can change the channels with firewire. Works perfect me and completely reliable. Just another option. You can also record digital streams (including HD) via firewire. How many channels you can get and how well this will work will depend on your provider and box (which stations/programs have 5c encryption turned on).

[https://help.ubuntu.com/community/MythTV_External_Channel_Changer](https://help.ubuntu.com/community/MythTV_External_Channel_Changer)
[https://help.ubuntu.com/community/MythTV_Firewire](https://help.ubuntu.com/community/MythTV_Firewire)

Your setup looks fine to me. Every any plans to do HD? Digital audio (Dolby Digital, DTS via S/PDIF). You could get a windows MCE remote and receiver (well supported in Myth) for half the price of imon remote you listed.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16880100851](http://www.newegg.com/Product/Product.aspx?Item=N82E16880100851)
Even comes with IR blasters...
> 
BTW, anybody know of anything other than mce that might let me play/pause/record digital cable and watch dvds. While I'm at it, why not something that can index my media over the network and watch all my media files

MythTV :)

---

### Post by djrobthaman on 2007-11-15
Now I like the way you're thinking.  More stuff, less price.  GENIUS

---

### Post by djrobthaman on 2007-11-15
Unfortunately someone finished my cheap motherboard and hard drive... but it looks like I did okay with this list.

But what about playing dvds and videos that are on the network???

Is it easy to do that with or without mythtv?

oh... and do you have to type in a user name and password everytime you turn on mythbuntu or is there a way not to?

Thanks for the info

---

### Post by djrobthaman on 2007-11-15
> **newlinux said:**
> 
BTW, anybody know of anything other than mce that might let me play/pause/record digital cable and watch dvds. While I'm at it, why not something that can index my media over the network and watch all my media files

MythTV :)

Wait a second.  Didn't see that one.  So, mythtv can definitely do everything then and not need a keyboard or mouse (I just want to use the remote control)??

---

### Post by newlinux on 2007-11-15
> **djrobthaman said:**
> Wait a second.  Didn't see that one.  So, mythtv can definitely do everything then and not need a keyboard or mouse (I just want to use the remote control)??

Yes. Now by playing dvds over the network do you mean ripped dvds? Then the answer is definitely yes. You'll want to use the mythvideo plugin, which is part of mythbuntu. 

[http://www.mythtv.org/wiki/index.php/MythVideo](http://www.mythtv.org/wiki/index.php/MythVideo)


It's pretty sweet if you ask me. I have 5 frontends and 3 backends (thus inexpensive is very important to me - I built mine mostly with used parts). All of them only contolled with a remote. I have over 500GB of dvds, home movies, and various video  formats and pictures that I access from any frontend. (pictures via mythgallery plugin).

I don't do it this way, but you can configure autologin with mythbuntu (my primary mythboxs are always on, and the other ones I also use as regular desktops). It's all in the mythbuntu and community mythtv ubuntu documentation. So you don't have to supply a password and username.

---

### Post by djrobthaman on 2007-11-15
This sounds great!!!  I think I might embark on this little project very soon.

When I said DVDs I meant real DVDs though.  I do have some of my DVDs ripped, but most of my collection are still discs and I would just want to use this machine as a back end and a front end and pop the DVD in the drive and have it play, all using the remote.  Hopefully there's no problem with the encryption though

---

### Post by newlinux on 2007-11-15
Well, if you are talking about playing the dvd through the dvd drive in the frontend, that's not a problem either: i do that. I thought you might be trying to play them through a drive on another machine over the network, which is doable, but more difficult:

[http://www.mythtv.org/wiki/index.php/MythDVD](http://www.mythtv.org/wiki/index.php/MythDVD)

Via remote.

---

### Post by newlinux on 2007-11-15
If you install the proper codecs and libdvdcss2 you shouldn't have a problem playing most non-DRM files and encrypted dvds.

---

### Post by djrobthaman on 2007-11-15
Nice.  Thanks for all the help

---

