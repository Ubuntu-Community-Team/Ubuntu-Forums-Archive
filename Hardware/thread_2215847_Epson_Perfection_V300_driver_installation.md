---
title: "Epson Perfection V300 driver installation"
date: 2014-04-08
forum: Hardware
---

### Post by rbmoler on 2014-04-08
I'm still a novice, but I thought I had this figure out.  I'm running Ubuntu 12.04 64bit.  I downloaded (from the Epson site)  iscan-data_1.27.0-1_all.deb and it installed.

I downloaded iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb.  I double clicked it, but the install process didn't start.  I tried the ltdl3 version as well.  Nothing.  (I couldn't find an answer to which of the two to use.)  Do I have to manually install it in a terminal or is there something else going on.?

Thanks in advance for any advice.

---

### Post by rbmoler on 2014-04-08
I read some more and now know I must use the "ltdl7" version of iscan.  I fiddled around some more.  Rebooted Ubuntu and tried installing iscan_2.29.3-1.........again.  This time it installed.  So optimist that I am I assumed that all was well.  Not so.  I get the message "Cannot send command to device."

So now what?  Probably read some more and see if I can find anything to fix it.

---

### Post by pdc on 2014-04-08
well done to get so far and get the data package installed first

>  I downloaded iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb

........ you were right to use that; ltd7 is for newer kernels; ltd3 is for much older kernels

what about open your Downloads folder from your desktop; right-click on the iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb

does "open with gdebi package installer" show ...... that should do the installing?

I guess the command way would be; open terminal and
[COLOR="#FF0000"]cd Downloads
sudo dpkg -i iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb[/COLOR]

---

### Post by rbmoler on 2014-04-08
Thanks for replying.  I had previously downloaded the interpreter [COLOR=#ff0000] esci-interpreter-gt-f720_0.1.1-2_amd64.deb[/COLOR].  I had read something about needing it, but the Epson site didn't indicate it.  I installed it anyway and LO! the scanner works.

I'm getting the hang of things little by little.

I don't relish having to use the terminal - too darned easy to make a mistake with such long involved and usually almost completely meaningless (at least to me) strings.  I have that command string written down (very carefully), but was hoping that Ubuntu would be kind to me and take over the job, which it did.

---

### Post by pdc on 2014-04-08
glad it is working; enjoy

> too darned easy to make a mistake  ....that's why folks will sometimes type out the commands and you can just copy and paste; 

You can edit the title of your thread to SOLVED if you wish (as it is your thread)

---

### Post by rbmoler on 2014-04-08
Thought I had done that.   Will try again.

---

