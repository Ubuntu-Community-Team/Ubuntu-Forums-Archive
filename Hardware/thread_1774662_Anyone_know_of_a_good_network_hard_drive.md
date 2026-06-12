---
title: "Anyone know of a good network hard drive?"
date: 2011-06-03
forum: Hardware
---

### Post by Kri5 on 2011-06-03
Hi,

I'm looking for a network hard drive to use on my home network to backup files between 3 PC's, 2 of which are running Windows, 'XP' and the '7', the 3rd is running Kubuntu 11.04.

Normally i would have no trouble choosing one for the Windows machines but I'm concerned that what ever i get may not work with Linux/Kubuntu.

Is anyone out there using a Network storage device?

I am particularly interested in something that will connect via Ethernet to my Virgin Super Hub and will be recognized by both Windows and Kubuntu.

I am not really interested in any bundled software on the device and would actually prefer there not to be any.

Any help and guidance would be greatly appreciated.

Thanks in advance, Kris.

---

### Post by collisionystm on 2011-06-03
any of these.

[http://www.buffalotech.com/products/network-storage/linkstation/](http://www.buffalotech.com/products/network-storage/linkstation/)

---

### Post by wolfen69 on 2011-06-03
You don't need another computer for this. Just add another hard drive to the computer of your choosing, and network it. It amounts to the same thing, and is cheaper.

---

### Post by elliotbeken on 2011-06-03
I agree buffalo has worked well for me everyday for the last 3 to 4 years, i also have an iomega which is not so good :(

---

### Post by Kri5 on 2011-06-04
The Buffalo looks like a good solution, I'm seriously considering one if the link stations. 

 However Wolfen69 has a good point, I could just share one of the hard drives on my XP machine. I'm not that familiar with samba however, I had a dabble before and could not get it working.

---

### Post by Kri5 on 2011-06-04
Thanks for the advice and thanks to Wolfen69 for reminding me about sharing the hard drive on my old tower running XP.

My previous experience of Samba wasn't great, fortunately however Kubuntu 11.04 appears to have everything installed and working out the box and i can see the shared documents folder, not only that but i have managed to use KRDC to remote into the old PC and set up the exceeding large spare hard drive as a shared network drive, result!

I'm happy for now, although the Buffalo is something to consider for the future, as i believe that should allow me to use my printer wirelessly, something my Belkin Network USB Hub doesn't.

---

### Post by The Flying Penguin on 2011-06-04
How do you plan to use your NAS?

Are you just looking to easily create a second backup of all your documents and personal photos and videos or are you wanting to use it to store everything instead of on your computers? If you are planning to store the sole copy of your files on it then you are definitely going to want a NAS with RAID support. That way if one of your drives in the NAS fails you won't lose your data. If you are planning to keep the files on the NAS and your computers so you have two copies then I wouldn't worry about getting one with RAID support.

Do you want to use it as a server for media like movies and music? How much space do you think you need? What about in the coming years?

Those prebuilt NAS units are really nice if you just want something simple and hassle free but they do have their downsides, most notably expansion limitations.

If you are looking to have some fun you could always repurpose an old machine and setup a server :P. Maybe a Linux server? Or you could always run something like FreeNAS which is very simple to use. That would be the most cost effective way to go and would offer the most expandability options and complete control over the software it runs and what it can do for you.

Anyway, once we know how you plan to use it and what your needs are, we will be able to better point you in the right direction.

Oh, and by the way. I wouldn't use a shared hard drive on a Windows machine in place of a NAS, especially if it is for backup purposes. That drive will be susceptible to viruses. If you have to go the shared hard drive route, I would without a doubt do it from your Linux machine.

---

### Post by Kri5 on 2011-06-05
I was originally looking for some where else to store all my pictures, as the hard drive on my Linux laptop isn't that big.  I was going to use my old Windows XP machine as it has a considerably larger hard drive.  I also have an external USB2 hard drive that i use to have attached to the XP machine for backups.
 
I understand that the Windows machine is undert hreat from Viruses and that my Linux laptop would be safer and i have thought of converting my old PC to linux also, although i have kept it so far for the old Windows games i use to play.
 
This 'FreeNAS' sounds interesting do you have more specific details or a link?
 
I presume i could use the XP machine to store my pictures etc and then have that machine backed up onto the external hard drive.

---

