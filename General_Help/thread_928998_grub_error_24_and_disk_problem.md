---
title: "grub error 24 and disk problem"
date: 2008-09-24
forum: General Help
---

### Post by phira on 2008-09-24
hello everybody

with ubuntu I learned to be patient:
I know very well that most of times the datas are safe (I had some crashes and I always fixed them)
BUT
in this case I begin to fear


history:

I am using ubuntu since version 6.06 and now I work with ubuntu 8.4 
Having boot problem with initramfs I tried several solution in order to fix it
suddenly after a reboot GRUB freeze with error 24 (error not found in the doc)

I am now using the live CD of 7.04 (thanks for it)

I tried to fix it with most of the solutions proposed here but no one works
supergrub disk can't reinstall grub 


I then try this
> ubuntu@ubuntu:~$ sudo fdisk -l 

Disque /dev/hda: 203.9 Go, 203928109056 octets
255 têtes, 63 secteurs/piste, 24792 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hda1   *           1       12305    98839881   83  Linux
/dev/hda2           24416       24792     3028252+   5  Extended
/dev/hda3           12306       24415    97273575   83  Linux
/dev/hda5           24416       24792     3028221   82  Linux swap / Solaris

Les entrées de la table de partitions ne sont pas dans l'ordre du disque
ubuntu@ubuntu:~$ 

then I tried this
> 
grub> root (hd0,1)
grub> setup (hd0)
Error 17: Cannot mount selected partition
grub> root (hda1)
Error 23: Error while parsing number

grub> 



I think that I have to reinstall whith reformating My machine 
but in this case, I absolutely need to save my datas before

my questions are: 
1/ who could help me before I desesperate? :)
2/ how can I fix my problem?
3/ if I can't, how can I save my datas?


thanks for your help

---

