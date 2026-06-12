---
title: "Tried installing gfxboot, now error 15"
date: 2008-11-21
forum: General Help
---

### Post by tstack77 on 2008-11-21
Following the same tutorial I've used for both gutsy and hardy ([HERE]("http://tuxenclave.wordpress.com/2008/01/18/how-to-install-gfx-grub-in-ubuntu/")), I've run into problems with intrepid.

I got to the point where I am to restore GFX grub (because I removed grub earlier), and I get:

[I]grub> find /boot/grub/stage1

Error 15: File not found[/I]

Since I already know my partitions I figured I could pass this step...nope.

[I]grub> root (hd0,4)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 2: Bad file or directory type[/I]

I looked in my grub folder and the file 'stage1' IS there :confused:

Ideas?

---

### Post by caljohnsmith on 2008-11-21
Most likely you are getting that Grub error 2 because Intrepid formats its ext3 partitions to use the newer 256 byte inode size file system standard, rather than previous versions of Ubuntu (including Hardy) that used a 128 byte inode size. So what does *that* mumbo-jumbo mean, right? :) The bottom line is that the Grub version in both Hardy and Intrepid can handle the newer ext3 partitions, but previous versions of Grub choke on it with an error 2. And because Grub can't read the new ext3 partition, that's probably why Grub can't find your stage1 file. 

That gfxboot tutorial you followed most likely uses an earlier version of Grub that can't handle the newer 256 byte inode size ext3 partitions. You would need the stage1.5 and stage2 files of the newer Grub versions to access the newer ext3 partitions. Since I don't know much about gfxboot, I unfortunately can't give you any workarounds or hacks other than to simply install a version of Grub that works with the new ext3 partitions. If you do find a way to hack gfxboot so that it works with the new ext3 partitions, it would be great if you can share your solution so everyone can benefit. :)

---

### Post by tstack77 on 2008-11-21
Wow, so very, very far over my head. Thank you for the explanation but unfortunately I must leave the workaround to others more qualified than myself (I break things).

It is a shame though that I can't find anything about gfx grub for intrepid with google, it really made the initial grub selection screen a whole lot prettier :)

Will a simple 'sudo apt-get install grub' get things back to normal?

---

### Post by caljohnsmith on 2008-11-21
I would do:
```
sudo apt-get purge grub
sudo apt-get install grub
sudo grub-install /dev/sda --recheck
```
You'll need to include that grub-install command because that is what actually reinstalls your Grub's stage1, stage1.5, and stage2 files to your MBR and /boot/grub folder (the MBR will only have the stage1 and stage1.5 file after it, but the /boot/grub folder will have all the files). Let me know how it goes. :)

---

### Post by tstack77 on 2008-11-21
I did what you said and all is perfect. 

And as a bonus, I just so happened to find a newer version of gfxboot for intrepid [HERE]("http://sidux.com/debian/pool/main/g/grub-gfxboot/")

THANKS again caljohnsmith!

---

### Post by caljohnsmith on 2008-11-22
> **tstack77 said:**
> I did what you said and all is perfect. 

And as a bonus, I just so happened to find a newer version of gfxboot for intrepid [HERE]("http://sidux.com/debian/pool/main/g/grub-gfxboot/")

THANKS again caljohnsmith!
Thanks so much for sharing your solution--that's a great find, because I didn't know if there was an updated gfxboot Grub that could handle the newer ext3 partitions. I'm glad to see there is one available, so if anyone asks again, I can steer them in the right direction. Cheers and enjoy your fancy Grub menu. :)

---

### Post by evilminininja on 2008-12-22
I love this thread so much!!! Thank you all, I am so glad i am not the only one that had this problem. I am currently downloading something and can't restart just yet... but everything seemed to work just fine in the terminal! :) maybe i can retry to install gfx after this and NOT mess up

---

### Post by tiberiup on 2009-02-03
hi, i haved that problem with old version of gfx grub...now i installed the new version that you linked above :
after install :
grub> find /boot/grub/stage1
 (hd2,0)

grub> root (hd2,0)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd2)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd2) (hd2)1+15 p (hd2,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

when i reboot i have grub error 2  ...any ideas ?

LE : i reinstalled and now i have no erros, this is strange :)

---

### Post by Malac on 2009-04-26
I downloaded this deb file from sidux.com:
[grub-gfxboot_0.97-40_i386.deb]("http://sidux.com/debian/pool/main/g/grub-gfxboot/grub-gfxboot_0.97-40_i386.deb")

Uninstalled GRUB then installed the deb using GDebI (just double-clicked on it)
Then altered the gfxboot-theme-zen(installed via synaptic) using the jaunty GDM background and GIMP then compiled it to this one.
[ATTACH]111198[/ATTACH]

Hope this helps

---

### Post by karllv on 2009-04-26
> **Malac said:**
> I downloaded this deb file from sidux.com:
[grub-gfxboot_0.97-40_i386.deb]("http://sidux.com/debian/pool/main/g/grub-gfxboot/grub-gfxboot_0.97-40_i386.deb")

Uninstalled GRUB then installed the deb using GDebI (just double-clicked on it)
Then altered the gfxboot-theme-zen(installed via synaptic) using the jaunty GDM background and GIMP then compiled it to this one.
[ATTACH]111198[/ATTACH]

Hope this helps

see you again:P

---

