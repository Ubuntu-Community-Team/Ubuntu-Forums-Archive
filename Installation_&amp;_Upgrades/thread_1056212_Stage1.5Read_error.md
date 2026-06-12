---
title: "Stage1.5Read error"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by meebers on 2009-01-31
New user.  I have a desktop, a single HDD in which I am trying to install 8.10.  I have tried 7.10, 8.04 and now 8.10 with same error Stage 1.5Read error.  The Live CD works normal.  Installation was with all defaults, HDD was freshly formatted.  I read some of the other posts, and if I understand it correctly, I can use the Live CD, and do the command "sudo bash ~/Desktop/boot_info_script*.sh" producing a results.txt??  What would I be looking for?....sorry newbe here.

---

### Post by caljohnsmith on 2009-01-31
You first have to download the "boot_info_script*sh" in order to run it, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

