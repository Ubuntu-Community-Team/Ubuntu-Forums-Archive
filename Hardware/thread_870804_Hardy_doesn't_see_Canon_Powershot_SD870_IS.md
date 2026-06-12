---
title: "Hardy doesn't see Canon Powershot SD870 IS"
date: 2008-07-26
forum: Hardware
---

### Post by Jorenko on 2008-07-26
When I first got my camera (Canon Powershot SD850 IS), I was already running hardy beta. It worked perfectly. It continued working perfectly until this week.

I have two up to date hardy machines that now both refuse to see the camera. On both, lsusb returns nothing new after plugging in the camera and gphoto2 --list-ports returns only this:
```
Devices found: 7
Path                             Description
--------------------------------------------------------------
disk:/                           Media 'Volume (ext3)'           
ptpip:                           PTP/IP Connection               
serial:/dev/ttyS0                Serial Port 0                   
serial:/dev/ttyS1                Serial Port 1                   
serial:/dev/ttyS2                Serial Port 2                   
serial:/dev/ttyS3                Serial Port 3                   
usb:                             Universal Serial Bus            

```

F-Spot and gthumb also both do not see the camera at all. dmesg and /var/log/messages both have no additional data in them after connecting the camera.

The last time I successfully imported photos was 5/31/08, so I suspect that something has been updated between then and earlier this week  ( let's say 7/22/08 ) that caused this.

Edit: The camera DOES recognize that it's been connected to USB, and both computers are still using other USB devices flawlessly.


Further edit: It seems that recharging the camera's battery fixed this. Very strange, considering it was showing full battery before I put it on the charger anyway.

---

