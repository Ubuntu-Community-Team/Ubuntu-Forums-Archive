---
title: "ubuntu update broke java in firefox"
date: 2008-07-29
forum: General Help
---

### Post by ethos_dacapo on 2008-07-29
This is total bs...
I spent countless hours trying to figure out how to get sound working in java applets on my laptop and the day after i fixed it ubuntu upgrades firefox rendering it utterly useless yet again. I'm very disappointed  in firefox 3 (and ubuntu 8.04 for that matter). The original fix was to go to the sun java site and download jre-6u10-beta-linux-i586.bin

After i unistalled the outdated ubuntu sun java package and installed the bin file from the sun website java had sound! But after ubuntu updated firefox i tested it to see if my sound would still work in java but it wasn't so i uninstalled and reinstalled the java package all over again hoping that would work like it did the day before but it didn't. I'm using it mainly in this website: [http://express.paltalk.com](http://express.paltalk.com)


When i first attempted to use this web version of paltalk i didn't even have java installed so it prompted me to install it, but i had the advantage of being able to see what loaded without java. I have sounds when i log on, when people message me, or they come online etc from the flash and everything else would work except when i went into a room there was no buttons for the volume or mic controls and it didn't show anybody on the mic. After i installed the sun java package from the repositories the java applet loaded and i had to verify that i wanted to use it on this site. It even showed that someone was on the mic but i still had no sound in the rooms. 

I hope this will be enough info for someone out there to be able to help me...


update: 
Ok get this... i installed the jre 6u10 build 25 java on my ubuntu desktop and now the sound works in it. It didn't work with the sun java package in ubuntu but its working with this updated version from the sun website. I have a feeling if i were to have an update for firefox in the future it would do the same thing as my laptop did today, breaking the sound in java. How can i do a fresh install of this java package from the sun website on my laptop? I tried deleting it from my home directory and deleting the sym link but that didn't seem to make a difference. Is there something i'm missing? Thanks for all your help ya'll

---

### Post by LowSky on 2008-07-29
Playing devil's advocate here 

You could use another browser like epiphnay, or opera or even go back to FF2.
I donn't know why your sound didn't work, but mine and many other sound does work in JAVA, but maybe instead of blaming Ubuntu for a bad release you could have disabled the upgrade to begin with, since you had a newer version locally installed.

---

### Post by ethos_dacapo on 2008-07-29
The update was for firefox not java... i'm downloading 6u10 build 28 (i had build25) to see if that fixes it. I have two different computers running the same version of ubuntu and java sound is broke in both of them, the java loads but i have no sound. When i run firefox 3.01 in windows it works fine. The main site i need sound on is [http://express.paltalk.com](http://express.paltalk.com) and it worked for the first time yesterday after installing build 25 from the sun website. The only thing that changed since then was the ubuntu update which was only firefox, not java... any ideas?

---

### Post by ethos_dacapo on 2008-07-29
ok installing jre 6u10 build 28 didn't work at all so i went back to build 25 which was working yesterday i recognizes that java is present but i still have no sound... this is very frustrating i hope somebody out there can help me before i go bonkers

---

### Post by stchman on 2008-07-29
> **ethos_dacapo said:**
> This is total bs...
I spent countless hours trying to figure out how to get sound working in java and the day after i fixed it ubuntu upgrades firefox rendering it utterly useless yet again. I'm very disappointed  in firefox 3 and ubuntu 8.04 for that matter. The original fix was to goto the sun java site and download jre-6u10-beta-linux-i586.bin

After i unistalled the outdated ubuntu sun java package and installed this java had sound! So i tried repeating the same steps today after ubuntu updated firefox and i found that the java was once again broken, no sound!!!!

This is not acceptable at all... I don't know anyone personally who is happy with firefox 3. They should've sat on it until they were sure it would be up to par which it isn't. and ubuntu should have never included it in 8.04 especially when it was still beta, that was just pure stupidity. 

If i sound a little p*ssed  off its because i am. As much time as i spent searching for the answer to fix this problem, posted in the forum with no responses whatsoever, fixed it myself, and then have somebody come along and break it again!!! The funny thing is if ubuntu's repositories were up to date i wouldn't have had this problem in the first place. 
jre-6u10 is the most recent verses the ubuntu repository 6u6b, that means there have been several updates that haven't been added to the repositories which would fix alot of problem for alot of people. 

I hope somebody has some answers cause i'm getting really tired of spending hours trying to get stuff to work that works fine in windows and worked fine in ubuntu too before "upgrades" if you can really call them that.

So you are saying that Java broke Ubuntu sound?

I have gotten the recent updates and sound still works just fine.

---

### Post by ethos_dacapo on 2008-07-29
> **stchman said:**
> So you are saying that Java broke Ubuntu sound?

I have gotten the recent updates and sound still works just fine.

No, i'm saying the firefox update from ubuntu broke my sound in java, sound still works fine in flash and everything else.

---

### Post by tuxxy on 2008-07-29
Hvae you got a link to an example, as mine seems to functioning fine also

---

### Post by ethos_dacapo on 2008-07-29
[http://express.paltalk.com](http://express.paltalk.com) the sounds from flash work but when you go into a room it shows someone has the mic but but you can't hear them talking. I finally figure out how to get it to work yesterday and then that stupid update broke it.

---

### Post by ethos_dacapo on 2008-07-29
Ok get this... i installed the jre 6u10 build 25 java on my ubuntu desktop and now the sound works in it. It didn't work with the sun java package in ubuntu but its working with this updated version from the sun website. I have a feeling if i were to have an update for firefox in the future it would do the same thing as my laptop did today, breaking the sound in java. How can i do a fresh install of this java package from the sun website on my laptop? I tried deleting it from my home directory and deleting the sym link but that didn't seem to make a difference. Is there something i'm missing? Thanks for all your help ya'll

---

### Post by ethos_dacapo on 2008-07-29
still no sound in java applets on my laptop... i deleted the .java folder the sym links and the install from my home directory, reinstalled everything and its still a no go.

update: 
i ran firefox from a terminal and this is what i got 
ethos@Dacapo-laptop:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
java.lang.InterruptedException
	at java.lang.Object.wait(Native Method)
	at sun.plugin2.message.Queue.waitForMessage(Unknown Source)
	at sun.plugin2.message.Pipe.receive(Unknown Source)
	at sun.plugin2.main.server.JVMInstance$WorkerThread.run(Unknown Source)

(firefox:8211): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

---

### Post by ethos_dacapo on 2008-07-29
> **LowSky said:**
> Playing devil's advocate here 

You could use another browser like epiphnay, or opera or even go back to FF2.
I donn't know why your sound didn't work, but mine and many other sound does work in JAVA, but maybe instead of blaming Ubuntu for a bad release you could have disabled the upgrade to begin with, since you had a newer version locally installed.

i tried epiphany and opera and neither worked, opera didn't even load flash and epiphany loaded just like firefox does....

---

### Post by WestCoastSuccess on 2008-07-31
Likewise, just updated ubuntu and firefox is utterly and completely hooped. Flash doesn't work. The navigation buttons don't work. Sometimes (rarely) the menu bar works. All my passwords gone. All my bookmarks gone. Just completely screwed here.

Tried to downgrade via synaptic to 3.0b5 (I think) but it tells me it must uninstall a whole host of programs, including ubuntu desktop!

I'm on an AMD 64 with a (unfortunately!) updated version of hardy - help!

After a year and a half of ubuntu this is the first time I've had this kind of ms experience...

---

### Post by ethos_dacapo on 2008-07-31
> **WestCoastSuccess said:**
> Likewise, just updated ubuntu and firefox is utterly and completely hooped. Flash doesn't work. The navigation buttons don't work. Sometimes (rarely) the menu bar works. All my passwords gone. All my bookmarks gone. Just completely screwed here.

Tried to downgrade via synaptic to 3.0b5 (I think) but it tells me it must uninstall a whole host of programs, including ubuntu desktop!

I'm on an AMD 64 with a (unfortunately!) updated version of hardy - help!

After a year and a half of ubuntu this is the first time I've had this kind of ms experience...

try doing 
sudo apt-get remove firefox 

and then reinstalling it  
sudo apt-get install firefox
 
if that doesn't work goto your home folder, view hidden items and then cut the .mozilla folder and paste it somewhere safe for back up like your desktop. Now try firefox and see if the flash or any of your other settings are working... if that doesn't work you can always paste the .mozilla folder back into your home folder to restore the previous profile configuration

---

### Post by ethos_dacapo on 2008-07-31
I just checked my java today after ubuntu updated and now i have sound again, very weird...
But i'd still like to try and figure out what happened in case it happens again if anyone has any ideas...

---

### Post by WestCoastSuccess on 2008-07-31
ethos_decapo: thank you! I had previously tried uninstalling and reinstalling - no luck, but once I removed the ~/.mozilla folder, it was recreated upon starting firefox and all works well. 

In case anyone else is in this unfortunate position, to get my saved passwords back, I simply copied signons3.txt, key3.db, formhistory.sqlite, formhistory.dat and history.dat from my old (broken) profile into my new profile.

Again, thanks - you really saved me when I needed it - much appreciated!

Cheers!

---

### Post by ethos_dacapo on 2008-08-01
> **WestCoastSuccess said:**
> ethos_decapo: thank you! I had previously tried uninstalling and reinstalling - no luck, but once I removed the ~/.mozilla folder, it was recreated upon starting firefox and all works well. 

In case anyone else is in this unfortunate position, to get my saved passwords back, I simply copied signons3.txt, key3.db, formhistory.sqlite, formhistory.dat and history.dat from my old (broken) profile into my new profile.

Again, thanks - you really saved me when I needed it - much appreciated!

Cheers!

I'm glad i could help! It seems many peoples profiles have been getting broken in firefox 3. I know people using it on winslows and they had to create a new profile as well. I hope the firefox team learns from their mistakes so they're not doomed to repeat them in firefox 4. With all the problems many people i know are actually switching back to ie  on winslows! you can rush a good thing ;)

---

### Post by ethos_dacapo on 2008-08-02
Ok i actually figured something out....
On my laptop i have to stop the pulseaudio process in order to get sound in java. Whats up with that? lol

---

