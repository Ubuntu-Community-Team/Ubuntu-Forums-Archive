---
title: "PDA's-Palm or Windows Mobile?"
date: 2008-05-04
forum: Hardware
---

### Post by rcdeacon on 2008-05-04
I would like to know if there is anyone who is using a PDA with Hardy and if so which one works? I currently own a Dell Axim X3 which is a windows mobile product and I cannot get it to sync with Evolution. I believe a Palm based PDA will sync easier but do not know which one will be the best (E2 or TX?). Thank you for any input regarding this issue. Also if anyone happens to know how to get a windows mobile product to sync with Evolution and can steer me to some relatively easy to use directions I would appreciate that as well.

---

### Post by andytgeezer on 2008-05-26
I'd be really interested in knowing the answer to this one too as my Windows mobile just got dropped down a flight of stairs. 

Anyone have any recommendations for what to buy next that will sync with Ubuntu 8.04?

Thanks!

---

### Post by omegamike3 on 2008-05-29
I too am in the market for both the wife and I and was wondering what people's experiences were so far? :)

---

### Post by derailed1 on 2008-06-17
I have the treo 650 and I'm in the process of syncing it.  I've synced it once but I have no idea what I did and now it won't sink.  I'll have time next week to play around with it.  

Have you considered a linux based PDA?  I think Sharp has them.  I'm not sure how compatibale they will be with Ubuntu but I would be surprised if they weren't.  I also read in the near future there will be Ubuntu Mobile based phones and pdas.  Something to consider.

---

### Post by bingoUV on 2008-06-17
Linux based PDA has no guarantee at all of being compatible with Ubuntu for syncing purposes. Only the kernel is linux, rest of the structure around could be very proprietary, and that is what matters. Check explicitly for linux sync support even if it is linux based.

---

### Post by silvagroup on 2008-06-19
Well I tried a Blackberry,major pain to get set up for syncing, so I thought since my old Palm Tunsten E worked so well with my Kubuntu and K-Pilot that another Palm device would be a no brain-er. Wrong it's as big a pain as the Blackberry. I got a Palm Centro, K-Pilot crashes. However I can sync my Tungsten E with no problem.
So I would say go for the Tungsten E.
Oh of course the Centro and Tungsten work fine with XP, except my main OS has been Linux for about 6 years now so I guess if I want to use my new device I will need to export the date from my Kubuntu to XP so I can get it into the new device.
And from what I saw from Googling this is a very weak area for Linux systems still. There's nothing simple in using PDA's with Linux. I remember that setting up my Tungsten took several days of experimenting also, but K-Pilot never crashed like it does with the Centro.
That's more than .02 worth. Good luck and if you get something that works please post your experience.

---

### Post by silvagroup on 2008-06-19
I have something that works:
Yes I now have all my data from my Kontact on my new Centro, had to use Windows but if it works, why not.
Here's what I did:
Installed new Palm desktop software on my XP (native on laptop).
Then synced my Tungsten with the new desktop.
Then exported all the datebases.
Then synced my Centro and imported the data to the desktop for the Centro, comes up as a different user so you just can't sync over.
Now the problem is when my data changes on my Kubuntu Kontact I will have to sync my Tungsten to my Kubuntu then to my XP then export from my Tungsten so I can Import to my Centro, how wacky is that. Oh well at least that works.
Hope this helps somebody out. I have been messing around with syncing with the new devices for over two weeks now so this very convoluted process is really a great thing.

---

### Post by silvagroup on 2008-06-19
Some more information I have discovered:
thinking that maybe the sync problem with K-Pilot was some version issue or a lack of understanding about K-Pilot and it's configuration, I downloaded and installed Hardy ( currently I am using Gutsy). But unfortunately on a freshinstall with no other device yet setup on K-Pilot
the problem is exactly the same as it is in Gutsy.
So still stuck with a mess for syncing.
Unfortunately I use my organizer allot so Windows is once again looking like it may have to be my main OS until Linux can get it's act together with the pda issue.

---

### Post by lswb on 2008-06-19
I have an older ipaq, model 3955 runs PocketPC 2002, syncing with Hardy. I use the evolution plugin with multisync and can synce calendar/contacts/etc. I originally got this working about 2 years ago on a different system running dapper. With dapper, the synce-gnomevfs package also allows browsing of files on the ipaq from nautilus on the linux system. Gnome in Hardy has switched from the older gnomevfs (Gnome Virtual File System) to the newer gvfs. There is a syncegvfs package that alleges to provide the nautilus browsing feature to hardy but I have not tried it yet. There is also a package available from sourceforge.net called syncefs, which can be used to mount the ipaq as a filesystem that is then accessible via nautilus or any other normal method. I just started playing with this yesterday and got it to work but not without bugs and it is kind of slow also. Both the syncefs and syncegvs packages are beta or pre-production. On the dapper system I was also able to get synce & file transfer working via bluetooth. I have yet to try this with hardy but AFAIK it should work.

As one of the other posters mentioned, there is not yet a "standard" for PPC/WM/CE devices to interoperate with linux. From what I have been reading on various websites, different programs and versions of programs will be necessary depending on what version of WM or PPC your PDA is running. If you want automatic connectivity and syncing to happen when you plug in the device, you'll need to write a few scripts and udev rules too. 

I don't have any direct experience with Palm devices so I can't comment on them, but I don't see how it could be any more difficult :)

---

### Post by silvagroup on 2008-06-20
Maybe I should try multisync. 
Tried KitchenSync in the Hardy install and can't seem to get it to do anything at all, not even crashing, and I can't seem to find any documentation for it. It's just a gui for opensync so maybe knowledge of cli for opensync is what I need. 
Problem is time, I just wish Linux had something that worked with PDA's and PPC's out of the box. 
Of course Mac and Windows have software written by the manufacturers to work with their devices on those OS's (advantage Apple and Microsoft).

I wouldn't think the Palm would be such a big deal since Linux has had conduits for Palm for a very long time, but for some reason this mew Centro is not playing well with K_pilot like the old Tungsten did.
Could be that I need to get rid of the old Tungsten config? or something, that's what I am not sure about and there doesn't seem to be to much info on this either.
It seems I have hi jacked this thread, sorry, will post the problem else where.

So Tungsten E works well with Kubuntu and K-Pilot.

---

### Post by scrooge_74 on 2008-06-20
I got my HTC Touch Elf to sync Contacts, Calendar and Tasks with evolution

---

### Post by irw on 2008-06-20
I have a palm Tx which works fine under gnome.
I did sync it with Evolution, but that lost all my categories and made a bit of a mess of my diary as a result.
now I use jPilot and although the GUI is not the best, it works perfectly.

---

### Post by ederic on 2008-06-24
J-Pilot also works well with my Treo 650. :)

---

### Post by joshzam on 2008-07-02
I can vouch for irw, as I too have a Tx and have been syncing it fine with J-Pilot on gnome for years. The fact that nobody is developing for the Palm platform anymore makes me think that my Palm days are numbered but, as long as my Tx holds out, I'm very happy with what I have.

---

### Post by Lilithd on 2008-07-04
I have a Tungsten E2 and have absolutely no problems with JPilot and Multisync. I have never had any luck with Kpilot except to wipe out everything on my palm when I attempt to sync it. I am currently running Ubuntu Heron (8.04) and am very happy with it. My only problem is that I can't find anything to install pdf's on the palm so I can read them with Adobe Palm reader.

---

### Post by silvagroup on 2008-07-04
> nobody is developing for the Palm platform anymore makes me think that my Palm days are numbered joshzam Am afraid you are right. Just bought this centro so it too will have to last for awhile. And sadly it looks like the smartphone and pda's are all aiming at Microsoft for their OS's. Appears that for awhile Palm was looking at Linux but I think they have dropped that idea.

I would really like to get kpilot going with my centro. I have been using it for over 6 years. And the Tungsten E, K-Pilot and Kontacts worked flawlessly and still does.
As soon as I have a little time I'll install J-Pilot and give it a try, from what I have seen for posts that will work but then there goes my data that's on Kontact.

As for PDF's I think you can just copy them to your memory card, or copy them with the install tool, from I can see J-Pilot has that also.

---

### Post by Bruce M. on 2008-08-06
> **Lilithd said:**
> I have a Tungsten E2 and have absolutely no problems with JPilot and Multisync. I have never had any luck with Kpilot except to wipe out everything on my palm when I attempt to sync it. I am currently running Ubuntu Heron (8.04) and am very happy with it. My only problem is that I can't find anything to install pdf's on the palm so I can read them with Adobe Palm reader.

Try [CardReader]("http://www.mobile-stream.com/cardreader.html")

Have a nice day.
Bruce

---

### Post by pogo07 on 2008-08-22
I am using a Palm TX with 
Hardy without any problems.  I use the Gnome applet and Evolution.  I cannot figure out how to add other software or update palm programs that are on the TX however.
HLV

---

### Post by silvagroup on 2008-08-22
Chek this out, [https://bugs.launchpad.net/ubuntu/+source/gnome-pilot/+bug/74703](https://bugs.launchpad.net/ubuntu/+source/gnome-pilot/+bug/74703).
Idont't use usb so I haven't tried it.
I just use bluetooth transfer. Transfer prc to pilot and it's up and running.

---

### Post by wijit on 2009-08-01
While having no idea about Palm I've got some disappointing experiences with WM 2003. What I wanted to do is to transfer some files from an SD card pluged in an Ipaq 1930 to Jaunty via USB port. I followed threads like:
[http://ubuntuforums.org/showthread.php?t=90205](http://ubuntuforums.org/showthread.php?t=90205)
[http://ubuntuforums.org/showthread.php?t=444387](http://ubuntuforums.org/showthread.php?t=444387)
and a guide in:
[http://www.lvivier.info/SynceFS/](http://www.lvivier.info/SynceFS/).
I managed to get them connected but the software could not access the card which contained most of my data. Opensync plugin for legacy devices like the one of mine is not available in Jaunty's repositaries. I used odccm and synce-serial to make a connection. I can ping from ubuntu to WM, load a coda module and mount the file system without explicit error. However, I cannot even use ls command to list files. It gets freezed and shows it cannot access the "Storage Card" which is a symbolic link of the card presented in WM file system. I stopped my experiment here not because of having got no idea to solve the problem but thinking further that even I could get files transfered they were garbage still in the eye of ubuntu. If you have a PDA or PPC running WM make sure you have Windows and Activesync. Some files like *.pxl need conversion before they can be used on a desktop. Also as cheap card readers are all around files that need no conversion can be transfered without painfully installation and configuration of programs (packages).:P

---

### Post by scrooge_74 on 2009-08-03
I think you could have better results using a newer version of WM

---

