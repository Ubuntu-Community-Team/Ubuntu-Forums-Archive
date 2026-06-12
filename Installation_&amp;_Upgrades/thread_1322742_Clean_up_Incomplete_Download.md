---
title: "Clean up Incomplete Download"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by registerkar on 2009-11-11
I am a Linux Newbie

I was installing Bitdefender as I have Windows on other HDD
When installing the GUI I used
'sudo apt-get install bitdefender-scanner-gui' in Terminal

It was taking too long to complete the download (3hrs Estimated for 33Mb)
66% Download was Finished & I canceled it & downloaded the Deb file from Bitdefender website.

From where do i cleanup the 66% incomplete file?
Where is it stored on HDD...Please help
I like clean systems.

Please Help

---

### Post by coffeecat on 2009-11-11
It's more than likely that the partially downloaded file was autodeleted when you cancelled. But in case it wasn't, have a look in /var/cache/apt/archives. That's where the downloaded *.deb packages go.

---

### Post by registerkar on 2009-11-11
Thanks a Lot !!!...
I found the File...

---

