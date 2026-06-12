---
title: "Installing later versions of WINE"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by zenbachry on 2009-08-31
So, I've done my homework, found how to update to the later version of WINE through the forums. It took a while before I got impatient and told it to stop trying to update. I then decided to  check out the website. Maybe (just maaaayyybeeee....lol) there would be an alternative or an installer. They said to go through the software sources and blah blah blah. As I'm following the instructions, it clicks in my head "Hey 'tard, you've done this before, it didn't work!" I continued to proceed, thinking things might have changed. When I tried to download the key from the site...IT WOULDN'T DOWNLOAD! *smacks head on desk* ow. I figured there was something up with Firefox (sometimes it doesn't completely get the scripts or something from the site causing 'broken' links, failure downloads, etc), so I restarted Firefox and tried again. Nothing. Wouldn't download. Last time I tried to do it, for some reason or another I couldn't add the key.

So, I'm now posting here...is there...ANOTHER alternative? I also checked out the archive on their webpage, but I got a timeout. Which, I find funny 'cause on the bottom of the page it says
> Very fast and reliable webhosting for the APT repository is graciously provided by budgetdedicated.com. :lolflag:

Would it be possible that they are only available during a certain time? Just a thought. Silly, I know.

---

### Post by Partyboi2 on 2009-08-31
Hi, you could try
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
``` to add the key, but I suspect that the site is down as I get a fail to connect error when I try it.

---

### Post by zenbachry on 2009-08-31
Thats what the forum I found said. Thats when I got impatient and tried the site. I failed to say what forums, but it was these forums.

Thanks though.

---

### Post by zenbachry on 2009-09-01
Hm. Wine's site must have been having troubles. Works now.

---

