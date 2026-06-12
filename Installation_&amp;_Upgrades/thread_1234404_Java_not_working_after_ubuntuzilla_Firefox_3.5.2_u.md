---
title: "Java not working after ubuntuzilla Firefox 3.5.2 upgrade"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by b0w on 2009-08-07
Hello! i have been using Ubuntu 9.04 since 4 months now and everything its great the only problem i had its with firefox, firefox 3 wich comes by default on the release was causing some apps to crash and some times they just turned gray and then be back normal again it was annoying, but when i update to firefox 3.5.1 everything got solved and wow i lovee my ubuntu, but a week a go i got an update for the firefox 3 that comes by default obviously because i upgraded manually not via synaptic so I upgraded but oohh suprise my firefox 3.5.1 went back to 3, couldnt upgrade it this time so i went to the ubuntuzilla script and it did it all the only thing now its java stopped working and sometimes from time to time firefox suddenly closes just like that, i tried reinstalling all the java web plugins and it didnt solved it, also tried to make a link again to the java bin file and the mozilla plugin dir but didnt work neither, anyone know how can i fix it?

Hello! i upgraded to the new version of the firefox browser and since that java just stopped working, i tried to uninstall java and install it again but it didnt solve the problem, when i go to about : plugins on firefox java its there and it says its enabled but when i test on a web page it doesnt work, im leaving here a link of a shot of the about: plugins page.
Anyone can help, i will really appreciate it.
[http://img19.yfrog.com/img19/136/screenshotzgv.png](http://img19.yfrog.com/img19/136/screenshotzgv.png)
[http://img98.yfrog.com/img98/6290/screenshot1u.png](http://img98.yfrog.com/img98/6290/screenshot1u.png)
[http://img98.yfrog.com/img98/7226/screenshot2p.png](http://img98.yfrog.com/img98/7226/screenshot2p.png)
[IMG]http://yfrog.com/0jscreenshotzgvp[/IMG][IMG]http://yfrog.com/2qscreenshot1up[/IMG][IMG]http://yfrog.com/2qscreenshot2pp[/IMG]

---

### Post by nanotube on 2009-08-08
are you running 64bit or 32bit ubuntu?

if 64bit, then look at the ubuntuzilla faq for restoring your plugins:

[https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BFirefox.5D_What_happened_with_Flash_and_all_my_other_plugins.3F](https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BFirefox.5D_What_happened_with_Flash_and_all_my_other_plugins.3F)

in either case, to resolve the "random crashing", suggest starting with a fresh profile. just quit firefox completely, and move your ~/.mozilla directory out of the way.
 mv ~/.mozilla ~/.mozilla.backup

you'll have to restore your bookmarks and all that, though, out of the backup directory.

---

### Post by b0w on 2009-08-08
im running 32 im going to check for that and ill let you know, thanks!

---

### Post by b0w on 2009-08-09
Ok! i did what the FAQ on Ubuntuzilla's wiki says tried to install ia32-sun-java6-bin but sun-java6-jre replace it now, i tried to installing it but i already have it it says the version i got its already the newest one, as you can see on the images i posted in about: plugins i already have java and it says its enabled but it just doesnt work when i try it on a webpage.

---

### Post by b0w on 2009-08-10
Solved! I had two java plugins installed and they were having problesm working together, i just remove the Iced Tea Java web plugin from synamptic and everything worked fine again!

---

### Post by nanotube on 2009-08-10
cool - glad you figured that out. :)

---

### Post by v1nsai on 2009-08-12
I used ubuntuzilla too, first it broke my flash plugin so I downloaded it manually (the 64 bit plugin doesn't work on 64 bit for some reason, I put the 32 bit version in /opt/firefox/plugins/ and it worked) but java was broken when I uninstalled firefox-3.5 (shiretoko).  I tried putting firefox-3.5 back but that didn't fix it either.

I've installed and reinstalled sun-java6-plugin several times, but it doesn't do anything.  There is a link to the jre in /opt/firefox/plugins but the browser doesn't see it at all.

---

### Post by b0w on 2009-08-12
hey, i dont know if its going to work for you but worked for me, go on firefox and type   about : Plugin  with out the spaces aside the 2 dots, check if you have more than 1 web jaba plugin enabled, if you have more than 1 try uninstalling one via synaptic, sometimes they have errors working togehter, then check your java again.
Hope this help you!

---

### Post by v1nsai on 2009-08-12
Neh, not installed.  I did follow the link on the plugins page and it said to just create a symlink from libnpjp2.so (or something like that) in /opt/firefox/plugins.  I tried but it still isn't seeing it in Tools > Addons or about:plugins.  Bah.

---

