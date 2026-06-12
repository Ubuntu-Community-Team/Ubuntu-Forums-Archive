---
title: "How to get pics from Kodak Z730 in Ubuntu 8.04"
date: 2008-10-14
forum: General Help
---

### Post by perdubug on 2008-10-14
I saved some pics on a SD card via my office PC's card reader(the card reader is fixed in the PC,it's not removable).I want to copy those pics to my home's PC. Since I have no card reader in my home,I put the SD card in my Kodak Z730 and connected it to ubuntu 8.04(2.6.24-19-generic). But the 'Import photos' UI can detect the device but it shows 'No images found'.

I tried to set the camera's mode from PTP to mass storage and then it can be mounted as a removable disk. But there is no any mode related setting in Z730. 

So I tried to get those pics via gphoto2, but it also shows that there are no any files on the SD card.

perdubug@perdubug-desktop:~/Desktop$ gphoto2 -L
There is no file in folder '/'.                                                
There is no file in folder '/store_00010001'.
There is no file in folder '/store_00010001/DCIM'.
There is no file in folder '/store_00010001/DCIM/100KZ730'.
There is no file in folder '/store_00010001/DCIM/100KZ730/08-9-15'.
There is no file in folder '/store_00010001/MISC'.
There is 1 file in folder '/store_00020001'.
#1     DDISCVRY.DPS                    0 KB application/x-script
(The pics are saved in /store_00010001/DCIM/100KZ730/08-9-15 folder).

My question is how to set mode from PTP to mass storage? If your answer is NO, how to get those pics via gphoto2 or other applications? Thanks.

---

