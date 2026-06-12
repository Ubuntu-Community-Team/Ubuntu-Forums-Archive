---
title: "Receiving files over Bluetooth"
date: 2009-11-04
forum: Hardware
---

### Post by 5349U11 on 2009-11-04
In 9.04, i had no problems receiving files over bluetooth, i was using a program, not too sure of the name, however i did find a [screen shot of it]("http://news.softpedia.com/images/news2/Transfer-Files-With-Bluetooth-on-Ubuntu-3.png")

Then when updating to 9.10, this program was no longer installed, and i could not find a similar program, nor the original.

Could you suggest how i could now receive files over bluetooth on 9.10

---

### Post by bslaveboy on 2009-11-05
I had the same problem. I solved it this way:

install gnome-user-share

In System->Preferences->Personal File Sharing, enable "Receive files in Downloads folder over Bluetooth". I also enabled "Notify about received files" and set "Accept files: " to "Only for Bonded and Trusted devices"... but you might want to try with "Always" first.

HTH

bslaveboy
--

---

### Post by 5349U11 on 2009-11-05
cool, trying it out now. thanks seems to be working

---

### Post by Rabreu on 2009-11-30
Obexpushd also works. Just install it (sudo aptitude install obexpushd) and run it on the console.

---

