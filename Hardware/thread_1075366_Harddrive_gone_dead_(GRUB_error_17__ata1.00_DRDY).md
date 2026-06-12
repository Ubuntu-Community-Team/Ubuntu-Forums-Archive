---
title: "Harddrive gone dead? (GRUB error 17 / ata1.00 DRDY)"
date: 2009-02-20
forum: Hardware
---

### Post by atlefren on 2009-02-20
I have a problem with my kubuntu 8.04 install on a 4.5 year old toshoiba tecra a2 laptop, and i _think_ the cause is a dead (or nearly dead) hard disk. 

After leaving the computer on over the night I opened the lid again and found the computer not responding. The screensaver image waws frozen to the screen and no response on either mouse clicks or keyboard press (ctrl-alt-esc did nothing). 

So, I turned off the computer, waited a while and turned it on.. It got as far as displaying the GRUB text, then halted for 1-2 minutes and reported back 

"Error 17"

A google-search lead me to 
[http://www.3till7.net/2007/10/25/grub-error-17/](http://www.3till7.net/2007/10/25/grub-error-17/)
and thus I tried booting using a kubuntu Live CD.

The splash screen showed up and I chose "start or install kubuntu", the loading screen appeared, but after 20-30 secs the screen went black and text like 

Buffer I/O error on device sda, locical block 6
Buffer I/O error on device sda, locical block 7
Buffer I/O error on device sda, locical block 8

ata1.00: status: { UNC } 
ata1.00: status: { DRDY } 

end_request: I/O error, dev sda, sector 52

amongst other things 

Intertwened with these error messages came the normal
"setting up hardware abstraction layers [OK]"
that kubuntu usually displays on startup, and finally the desktop appeared.

i tried finding my disk, using 
 sudo fdisk -l
but this returned nada, nothing, null

Then i searched for ata1.00: status: { DRDY } etc and found that this probably meant that the disk was broken (see [http://ubuntuforums.org/showthread.php?t=892657](http://ubuntuforums.org/showthread.php?t=892657))

I then downloaded and burnt the ubuntu rescue remix live cd, same procedure as when booting the kubuntu live cd, error messages interrupt the normal messages. 

Still no disks found by fdisk, testdisk reports "no harddisk found"
running 
sudo e2fsck -C0 -p -f -v /dev/sda1
(I have/had two partitions, and i _think_ they where sda1 and sda2)
sets off a series of the beforementioned error messages again for a minute, then:
Attempt to read block from filesystem resulted in short read while reading block 24315
JBD: Failed to read block at offset 32002
e2fsck: Input/output error while recovering ext3 journal of /dev/sda

so, my question is: is it possible to salvage any data from this disk, or should i just toss it away? If possible I am thankful for any suggestions, hints or tips.

---

### Post by caljohnsmith on 2009-02-20
Since you don't know for sure whether the problem is with your HDD or something else with your computer, I would recommend pulling the HDD out, hook it up to another computer, and see if you have any luck accessing it from the other computer. Were you previously able to boot the Kubuntu Live CD, and only now it doesn't work? If so, that would suggest the computer has problems more serious than just your HDD.

---

### Post by atlefren on 2009-02-20
well, I am 95% sure it is the disk, but trying it on another computer might be worth a shot. 

Maybe I didn't explain very well, the Kubuntu LiveCD still works, just switched to the Ubuntu Rescue Remix to have access to more tools... Apart from the fact that the LiveCD-startup gets bombarded with messages from the Kernel about faulty sectors they seem to work fine..

---

