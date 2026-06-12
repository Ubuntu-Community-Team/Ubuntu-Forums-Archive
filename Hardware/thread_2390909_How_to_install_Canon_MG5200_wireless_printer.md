---
title: "How to install Canon MG5200 wireless printer"
date: 2018-05-03
forum: Hardware
---

### Post by steve.clay on 2018-05-03
I put the following post up on the forum. But I have since found the answer: it is critical to install cups-backend-bjnp. This package can be found on the internet and there is even a button to use apt to install it. After installing it the standard CUPS admin page finds the printer and installing it is just a matter of following the prompts.
So - if you have a printer like mine and are struggling to connect wirelessly, this may be the solution to your problem!

Here is my original post: now redundant.

Hi, so I installed fresh installation of 18.04 two days ago. It replaced an installation of 16.04 which had become a bit unstable. Installation solved all the problems, hooray! So now I need to reinstall my Canon MG5250 wireless printer. The Add button on the printer settings doesn't find it even though it is switched on and a couple of feet away from my laptop. All the advice I can find seems to be out of date. Typing in the connection details I wrote down before re-installing doesn't work. In short, I am stuck. One page suggested connecting by usb first (this worked) but then didn't explain how to go from a wired to a wireless situation. Any help or advice would be much appreciated. Thanks.

Adding fresh information in case it helps: have downloaded printer driver cnijfilter-mg5200Series_3.40-1_amd64.deb and installed it. Have tried to add printer using localhost:631 i.e. CUPS 2.2.7. But still stuck. Printer is not found. I printed out the wireless information from the printer's menu so have e.g MAC Address, SSID, IP Address. Even so, still not obvious (to me) what to do next. Tried filling in 'add printer' form on CUPS with socket://ip-address but it doesn't work...'printer not responding' when I try to print something. Any help would be much appreciated. Please? (I'm pretty sure that I installed the same printer on 16.04 and CUPS found the printer so I don't know why it is so hard this time.)

---

