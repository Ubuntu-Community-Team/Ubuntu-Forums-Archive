---
title: "why wireless problems with ubuntu?"
date: 2005-10-07
forum: Hardware &amp; Laptops
---

### Post by rscaramelo on 2005-10-07
I've tried various distros with my Compaq M2000 laptop but only Ubuntu gives me fits. I can't connect wirelessly. I've done the searches but the answers just confuse me being that I'm a linux nOOB. I have posted here before and people have tried to help. Given Ubuntu's objectives, this should be made much easier than it is. No problems with Linspire, Mepis, pclinuxos, Knoppix, etc. I want to use Ubuntu (actually Kunbuntu) because of the great reviews and the community here. The little I've been able to try has been great. The wireless problems are disappointing. There needs to be an EASY solution to this. 

Sorry about the whine.

RC

---

### Post by aysiu on 2005-10-07
I'm not sure what to tell you. If people have tried to help, that's about the most they can do. If you've tried to search and posed questions, that's about the most you can do. If I were you, I'd stick with a distro that works for your hardware. I happen to love Ubuntu, but if it wasn't recognizing my hardware and some other distro was, I wouldn't stick with Ubuntu too long.

---

### Post by Corvillus on 2005-10-07
It has the broadcom 4306 54g card, which means you'll have to use ndiswrapper to get the card installed. There is a thread on how to do this here: [http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683) (this card is notorious for being a pain to set up).

---

### Post by jwhorfin on 2005-10-07
I'm a 2 week old linux user and can build computers, and now fix them for everyone I know :rolleyes: 
I found Ubuntu Hoary amazingly simple to load on my Dell Inspiron 8200 excluding the 1 week I spent on getting my Broadcom 4306 Linksys WPC54g working. I read the wiki here, Ndiswrapper wiki, and read  and tried everything found in searches here. Trust me when I say everything, the only thing I didn't try was to fling it off the front porch like a frisbie into the sreet and watch it get mashed to a fine powder by the traffic ](*,) 
I used the bcmwl5.inf and bcmwl5.sys driver and always got to the point that the card was seen and working but could not connect to the network.
Make a long story short In windows some security circles say you should not broadcast your ssid from your wap. This was the answer for me. I enabled ssid broadcast and bingo it worked. It works with wep and with mac address lock-down. I  tried every combination of settings on the laptop and the wap and it was the ssid  all the time...good grief #-o 

Thanks to all of you who posted in those many threads :)

---

### Post by rscaramelo on 2005-10-07
I appreciate everything from the people here who have tried to help. My whine was more directed at the Ubuntu people who I wish could make this easier because the forums are littered with these problems. That said, I'm going to try some of the suggestions here.

Thanks,

RC

---

