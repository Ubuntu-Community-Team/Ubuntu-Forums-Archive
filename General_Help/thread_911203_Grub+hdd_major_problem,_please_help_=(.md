---
title: "Grub+hdd major problem, please help =("
date: 2008-09-05
forum: General Help
---

### Post by zenthor on 2008-09-05
Okey so heres my history.

Some time ago I decided to give Ubuntu a try, I installed it on my 40Gb HDD, and left the 60GB HDD that i have for media, so I had, 20Gb WinXPSP2, and other 20Gb on ubuntu+Swap. At the begin I had problems with Grub and I got it fix to boot correctly to WinXP, cause it didnt.

Time passed and i stopped useing Ubuntu cause most of my programs of University are for Windows. So yesterday I decided to plug in my CD reader, and put the WinXPSP2 Cd inside, and deleated the partitions where Ubuntu was, and SWAP too, cause I needed more space, and I got in Ubuntu and I didnt find a way to uninstall it.

I restart the computer and heres where all the "fun" begins.
First, Grub appears to still be on my system, and throws me error 17, while grub 1,5 was loading or something like that.
So I ran into my aunt computer to get help from forums, and in the Ask/Answer section i find more people with the same problem, and I anyways, posted my own, and i got replys about useing the following method:

Use Recovery Console from the WindowsXP installer CD.
Do the "fixmbr" command

This should repair you damaged mbr by the Grub.

So I did that, restarted the computer, and the problem was still there, but the grub error number changed, i cant remember very well if it was to 22... or 15.
So i read a little more, about this issue, and on the recovery console I do the "fixboot" command, and "bootcfg /scan" and "bootcfg /list" and "bootcfg /rebuild"(wich only adds an extra entry on the list, dosent change it completly), but to for my surprise, it didnt detect my old WindowsXP installation, only a uncomplete instalation of WindowsXp i had made before on the place where Ubuntu was (this i did afterfirst try with fixmbr, but couldnt complete instalation cause i couldnt boot to this new instalation, cause grub still got error)

So now, i read a little more and ask around, and i see the posible solution is copying a pair of files, from the WindowsXp installation CD, to the place I had my WinXP, such as this two:
cd drive:\i386\NTLDR (or simillar name i cant remember)
cd drive:\i386\NTDETECT.COM
I did both, and deleated the partition where the uncomplete winxp was. And still got nothing going on, grub still appearing with diferent problems.

So i give on asking on forums, and stuff and tryied to use a little logic in here, and i thought, re install Ubuntu, so it reinstalls grub, or repairs it, and then check if im able to boot to my old WinXp.
So i did so, and installed ubuntu+swap on 9GB, and left free space of about 11Gb, and at the end of the disc was the 20Gb partition with my WinXP. After successfully installed ubuntu, I entered ubuntu again to see if i had some more replys on my problem (cause after installing ubuntu, i tryied to boot to winxp with no luck, got problem saying couldnt find ejecutable or something like it), so I thought maybe i install a new winxp on 7gb from the 12gb i had free in the middle of the disk, so as it would be new installation, grub would see it, and i would have access to that new winxp partition, do a rescue of my files on the old one, and then deleat both, and install just one on all the space (stupid me, i could rescued the information from ubuntu already but i didnt notice back then), so i tryied to install again winxp, so i finish doing the "blue/yellow" part of it, and it asks me to restart the computer, so it was supoused to boot to the new winxp, finish installation and continue but here then i couldnt boot to the new or old winxp, so i then i try to boot to ubuntu to search for more help, and then it says cylindre out of maximum allowed by the BIOS, or simillar problem, something wrong with a cylindre so i proceed to deleat the "new" winxp partition, the old ones of the ubuntu and re install ubuntu again, with no luck, i tryied for 3th time and no luck, throws me again the same problems on the same partitions, if i try to boot to windows, it says there was no ejecutable or something like it, if i try to boot to ubuntu it says the problem with the cylindre out of BIOS.

So now im useing the LiveCD, i see my old winxp is ok, is still here, all complete aparently, and all the media on the 60GB HDD too, and i cant rescue my information from the livecd since i need to do an update to ubuntu so it recognizes my 20GB portable HDD/mp3 (toshiba GIGABEAT).

please help me, i dont know what else to do.

Maybe someone can guide me to edit from the livecd the grub, to check if its commands to mount points are ok, and try this, or a way to rescue my information from the 40gb hdd (on the 20 gb partition where the old winxp is), and then format the whole hdd correctly so the grub is gone, or will it remain since it is on the mbr? T_T

please please help me :'(

---

