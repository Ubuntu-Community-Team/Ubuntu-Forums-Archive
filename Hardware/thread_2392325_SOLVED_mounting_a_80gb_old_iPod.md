---
title: "SOLVED mounting a 80gb old iPod"
date: 2018-05-19
forum: Hardware
---

### Post by enrique-melero on 2018-05-19
Well, I think there are still people like me using really old hardware such as the unbreakables old ipods
I had issues mounting it read only after resetting it with iTunes. The mount command is buggy and it does not really tell you much if it fails to do what you instruct it to do
This is the command that worked for me to mount it read-write

$ sudo mount -v -t hfsplus  -oremount,rw,force /dev/sdc2 

I installed hfsprogs beforehand with 

$ sudo apt-get install hfsprogs

None of the proposed solutions here or anywhere else worked, so I thought it would be a good idea to post this
This is a log of all I tried until I found the right combination

2002  sudo mount --remount /dev/sdc2 -o rw
2004  sudo mount /dev/sdc2 -o rw,remount
2010  sudo mount  -o rw,remount /dev/sdc2
2012  sudo mount  -o rw,remount /dev/sdc2 /media/enrique/iPod\ de\ Enrique\ Melero/
2023  sudo mount -v -o rw, remount /dev/sdc2 /media/enrique/iPod\ de\ Enrique\ Melero/
2024  sudo mount -v -o remount, rw /dev/sdc2 /media/enrique/iPod\ de\ Enrique\ Melero/
2025  sudo mount -v -o remount,rw /dev/sdc2 /media/enrique/iPod\ de\ Enrique\ Melero/
2029  sudo mount -t hfsplus -o rw,remount -force /dev/sdc2 /media/enrique/iPod\ de\ Enrique\ Melero/
2031  sudo mount -v -t hfsplus -o rw,remount -force /dev/sdc2 /media/enrique/iPod\ de\ Enrique\ Melero/
2036  sudo mount  -o remount,rw -force /dev/sdc2 
2038  sudo mount -f  -o remount,rw -force /dev/sdc2 
2047  sudo mount -t hfsplus -f  -o remount,rw,force /dev/sdc2 
2055  sudo mount -v -t hfsplus -f  -o remount,rw,force /dev/sdc2 

And this is the one that works (note the no space after the -o) :
sudo mount -v -t hfsplus  -oremount,rw,force /dev/sdc2

Hope it helps others

---

