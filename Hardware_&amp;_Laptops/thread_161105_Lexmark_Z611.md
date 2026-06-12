---
title: "Lexmark Z611"
date: 2006-04-16
forum: Hardware &amp; Laptops
---

### Post by giddy1945 on 2006-04-16
I followed the instructions on this thread: [http://ubuntuforums.org/showthread.php?t=159704&highlight=lexmark](http://ubuntuforums.org/showthread.php?t=159704&highlight=lexmark)

Everything worked fine.  If you read the replies that I posted, you will see my problem.
The printer is connected  directly to my box via USB cable.  The driver shows up in the printer set up list, and I am using it.  Everything on my monitor looks normal when I initiate a test page or attempt to print a text document or picture, but the printer will not respond at all.
 I have only been into computers for five months, and have been running only Linux. Please keep that in mind when you respond. Thank you all for the great support.
By the way, I do not understand what is meant by,"devfs will not run on boot" when I installed it with synaptic; however, when researching how others got the Z611 to work they bring devfs up, as in "works with devfs", and if it makes any difference I am using the regular account, not root.  I understand that you must be in root(offline) in order to tweek and peek certain aspects and that Ubuntu is set to not use root by default.  I have not yet figured out how to use root.

---

### Post by giddy1945 on 2006-04-17
I am researching how to run as root; however, any help on the printer problem would be greatly appriciated if root has nothing to do with it.

---

### Post by black hole sun on 2006-04-21
[QUOTE=giddy1945]I am researching how to run as root; however, any help on the printer problem would be greatly appriciated if root has nothing to do with it.[/QUOTE]
Root doesn't have anything to do with anything as far as you are concerned ;)

Please post the contents of this command (you have to run it in a terminal):

 /usr/lib/cups/backend/z600

---

### Post by Sef on 2006-04-23
Look at this tutorial for the Z600 series.

[http://www.ubuntuforums.org/showthread.php?t=159704&highlight=lexmark]("http://www.ubuntuforums.org/showthread.php?t=159704&highlight=lexmark")

---

### Post by Jennabob on 2006-08-28
"The printer is connected directly to my box via USB cable. The driver shows up in the printer set up list, and I am using it. Everything on my monitor looks normal when I initiate a test page or attempt to print a text document or picture, but the printer will not respond at all."
 
Im having the same problem as giddy1945 and when i type in

/usr/lib/cups/backend/z600

into the terminal i get nothing! please help ](*,)

---

### Post by McHenry on 2006-10-12
Hi guys...

I have followed the Lexmark howto under Dapper and still get no output from ./z600 Accordingly I am still unable to print. I have noticed this seems to be quite a common symptom however I have not found a resolution.

root@laptop:/usr/lib/cups/backend# ls -l
total 188
-rwxr-xr-x 1 root root   7199 Apr 12  2006 beh
-rwxr-xr-x 1 root root   9768 Mar 20  2006 bluetooth
-rwxr-xr-x 1 root root  10300 May  4 04:41 canon
-rwxr-xr-x 1 root root  10308 May  4 04:41 epson
-rwxr-xr-x 1 root root  18416 Apr 27 20:40 hp
lrwxrwxrwx 1 root root      3 Sep 29 16:58 http -> ipp
lrwxrwxrwx 1 root root     24 Sep 29 16:58 ipp -> ../backend-available/ipp
lrwxrwxrwx 1 root root     24 Sep 29 16:58 lpd -> ../backend-available/lpd
lrwxrwxrwx 1 root root     29 Sep 29 16:58 parallel -> ../backend-available/parallel
lrwxrwxrwx 1 root root     21 Sep 29 16:58 smb -> ../../../bin/smbspool
lrwxrwxrwx 1 root root     27 Sep 29 16:58 socket -> ../backend-available/socket
lrwxrwxrwx 1 root root     24 Sep 29 16:58 usb -> ../backend-available/usb
-rwxr-xr-x 1 root root 119011 Aug 21  2003 z600
root@laptop:/usr/lib/cups/backend# ./z600
root@laptop:/usr/lib/cups/backend#


Any help would be greatly appreciated I can assure you :)

Thanks

---

