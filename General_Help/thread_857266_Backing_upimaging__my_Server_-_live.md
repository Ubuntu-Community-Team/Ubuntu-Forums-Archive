---
title: "Backing up/imaging  my Server - live"
date: 2008-07-12
forum: General Help
---

### Post by hcclnoodles on 2008-07-12
Hi there

I have a webserver running under Ubuntu and I want to back up my system in an "image" type format so i can recover it to its last known good state, but using 'partimage' I am not allowed to create an image of the root filesystem unless I unmount it, which obviously i cant do because the webserver is up 24/7

I have an smb network mount already to go on the box so that i can send my 'image' file over the network to a backup box, but thats no good if I cant create an image of a running file system in the first place

Is there any way I can do this..? I know I can just back up my data files etc, but that would involve having to rebuild Ubuntu from the CD, reconfigure everything to the way it was (which will take ages) and then restore all my data files back on again ....not good :-(

any help would be greatly appreciated

---

### Post by boblemur on 2008-07-12
you can go on live cd... and you can do it from there... but that means bringing the computer down still... 

it doesn't seem very possibly, although have u tried just copying the / directory minus like media and mnt and things like that... and then after you have a copy of it... just pack that...

but i doesn't seem like a very nice solution

---

### Post by hcclnoodles on 2008-07-12
Thanks boblemur, I just dont have the confidence that tarring up / will be sufficient ...plus, how would I restore it, Id have to rebuild ubuntu still from the CD and then untar it from / which im sure wouldnt let me write to a lot of the running system files...

The other slight issue I have is that the server has no CD rom drive  and the whole disk is partitioned as one partition (/) which means that even if i did boot from CD, i wouldnt have an alternate backup partition to put my image on (and apparantly part image wont let you put your image file on the partition which your curently backing up, which I guess makes sense)

bad design i know, but i will correct that one day

---

### Post by boblemur on 2008-07-12
kinda over kill but if you have physical access to it... you could put in a second drive... and see if you can copy the entire thing over... and then if you need to change to the other image... just edit your /boot/grub/menu.lst

to default to boot the other drive...

kinda another not so good solution... but i dont see how you could do this any other way :S

im still rather new to linux however so i could be wrong...

because in theory you should be able to read the entire disk... while its running...so you can copy it... but yeh i dono :P

---

### Post by hcclnoodles on 2008-07-12
thanks, can anybody reccommend any other backup / imaging utiliies other than partimage that may help achieve this ?

---

### Post by lordadi on 2008-07-23
I recommended clonezilla somewhere else but it runs off a cd and would mean bringing down your server. hmm...

---

