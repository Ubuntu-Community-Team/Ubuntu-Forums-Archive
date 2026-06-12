---
title: "iso will not load..."
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by medicalystoned on 2009-05-24
I am trying to install an iso I downloaded. It is stored in my documents, i opened it with kpackagekit, I click yes to install, it begins then a message pops up saying an internal error occured and when i close that window it just closes the program.... any suggestions would be greatly appreciated. Thank you all in advance..



Thank you everyone, I will burn in and then load it.......thanks again.

---

### Post by logos34 on 2009-05-24
what exactly are you trying to install?

---

### Post by lisati on 2009-05-24
iso files usually go straight to CD or DVD, have a look here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by medicalystoned on 2009-05-24
> **logos34 said:**
> what exactly are you trying to install?

someone gave me a link to Ubuntu Stoner edition, i downloaded it and would like to try it and see what it is like. Thanks again for any help....

---

### Post by medicalystoned on 2009-05-24
> **lisati said:**
> iso files usually go straight to CD or DVD, have a look here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Thanks for the info, I checked that out but I was wondering if I have to burn the iso on a disk first or is there a way to install it from where it is now? Thanks again for the help.

---

### Post by pebo on 2009-05-24
Try this:
```
sudo mkdir /mnt/image
```
```
sudo mount -t iso9660 -o loop /path/to/image.iso /mnt/image
```
Open /mnt/image in your file manager
hth

edit: don't forget to umount image when finished
edit2: sorry, didn't read your post carefully. I think you will have to burn it to cd to boot into it

---

### Post by medicalystoned on 2009-05-24
> **pebo said:**
> 

edit2: sorry, didn't read your post carefully. I think you will have to burn it to cd to boot into it

no problem... so I did all that, is there anything I need to do now, ie. unmount? how do i do that if yes?  Thanks again for the help.

---

### Post by pebo on 2009-05-24
Yeah, if you mounted the iso as in my instructions```
sudo umount /mnt/image
```
Then I would use k3b to burn it to cd (Tools>Burn CD Image)
hth

---

### Post by Lolli Pop on 2009-05-24
Download Daemon Tools:
[http://www.daemon-tools.cc/eng/home](http://www.daemon-tools.cc/eng/home)

After You Download Install It And Now You Can Mount The ISO And Install It. You Can Even Boot Your Machine Up From That.

---

