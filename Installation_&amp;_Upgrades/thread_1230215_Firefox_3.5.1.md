---
title: "Firefox 3.5.1"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by Eumenides on 2009-08-03
I just downloaded the latest upgrade to firefox, version 3.5.1. But when i double click on the file it opens up in this windows that has "Archive" as one of the upper buttons and it also has an "Extract" button and a "Add Files" and "Add Folder" buttons. So im totally bewildered as to how to apply the upgrade. Please help.

---

### Post by smdeep on 2009-08-03
Hi
You will have to extract it to a directory (folder) and then run the file named firefox. I generally create a bin directory in my home directory, extract there and then open a terminal, navigate to the directory and run the file like this ./firefox.

Hope this helps

---

### Post by Eumenides on 2009-08-03
Thank you.
Can i inconvenience you with a couple more questions?

-I had extracted the files to a folder, but when i run the "Firefox" icon and then press run, it does nothing. So im doing what to do u suggested. I extracted the files to a folder titled "Firefox" in my home directory. Problem is, im fairly new to Linux, and i dont know how to use the Terminal properly, in so im not familiar with the commands with which to navigate to the "Firefox" folder i created and run it via terminal. Can you please tell me the commands i should use?

---

### Post by Partyboi2 on 2009-08-03
> **Eumenides said:**
> Thank you.
Can i inconvenience you with a couple more questions?

-I had extracted the files to a folder, but when i run the "Firefox" icon and then press run, it does nothing. So im doing what to do u suggested. I extracted the files to a folder titled "Firefox" in my home directory. Problem is, im fairly new to Linux, and i dont know how to use the Terminal properly, in so im not familiar with the commands with which to navigate to the "Firefox" folder i created and run it via terminal. Can you please tell me the commands i should use?
What version of Ubuntu are you using? If you are using jaunty you can install it from the Ubuntu repos by opening a terminal and
```
sudo apt-get install firefox-3.5
```
Another method to install is to add a 3rd party repo and install it. See [[COLOR=Blue]here[/COLOR]]("http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html").

---

### Post by lotster on 2009-08-03
I wholeheartedly recommend using Ubuntuzilla (look at [http://tombuntu.com/index.php/2009/07/15/install-firefox-35-in-ubuntu-904-using-ubuntuzilla/](http://tombuntu.com/index.php/2009/07/15/install-firefox-35-in-ubuntu-904-using-ubuntuzilla/)).  I got the new Firefox working the way you're trying, but as soon as I ran updates, and there were Firefox updates available, 3.5.1 was messed up.  Rather use Ubuntuzilla, trust me on this.

Or Partyboi2's way will also work... ;-)

---

### Post by smdeep on 2009-08-08
I tried Ubuntuzilla and it works perfectly. Highly recommended.

---

