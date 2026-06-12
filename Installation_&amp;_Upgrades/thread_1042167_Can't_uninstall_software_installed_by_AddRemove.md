---
title: "Can't uninstall software installed by Add/Remove?"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by abcuser on 2009-01-17
Hi,
I installed "Avant Window Navigator" from Application | Add/Remove. This software is really cool, but it doesn't work as it should on my PC. But on my PC main menu on left top of the window freezes - click on it does not display menu - when "Avant Window Navigator" is installed. Probably nVidia graphic driver problem. I have some other problems using compiz. So I decided to uninstall it but I was surprised I got error that uninstall via Application | Add/Remove is not possible because "other" software is dependent on Avant Windows Navigator packages and I should uninstall it using System | Administration | Synaptic Package Manager. Why??? I installed the software, tested it and I would like to remove it. I haven't installed any other software in the mean time that could be dependent on Avant Window Navigator. And if Ubuntu knows there are dependences why not remove only unneeded packages? How can I know which package is save to delete from Synaptic if Ubuntu can't?

Don't quite understand logic behind this remove software policy. Can someone explain me why is this default remove application behaviour?

Regards

---

### Post by skern03 on 2009-01-17
> **abcuser said:**
> Hi,
I installed "Avant Window Navigator" from Application | Add/Remove. This software is really cool, but it doesn't work as it should on my PC. But on my PC main menu on left top of the window freezes - click on it does not display menu - when "Avant Window Navigator" is installed. So I decided to uninstall it but I was surprised I got error that uninstall via Application | Add/Remove is not possible because "other" software is dependent on Avant Windows Navigator packages and I should uninstall it using System | Administration | Synaptic Package Manager. Why??? I installed the software, tested it and I would like to remove it. I haven't installed any other software in the mean time that could be dependent on Avant Window Navigator. And if Ubuntu knows there are dependences why not remove only unneeded packages? How can I know which package is save to delete from Synaptic if Ubuntu can't?

Don't quite understand logic behind this remove software policy. Can someone explain me why is this default remove application behaviour?

Regards

I just experienced the same thing attempting to remove an mp3 player. I don't know the reason, but I agree with your point. 

Add/Remove Programs is sorta like Synaptic Package Manager Lite. :P

My assumption (yes, I know what happens when you assume) is that Synaptic handles packages more thoroughly, and checks dependencies.

Unfortunately, we either cave in or tilt at windmills like Don Quixote. Or... you can post it as a bug on Launchpad and see what they say.

---

### Post by abcuser on 2009-01-17
@skern03, sure I have checked Synaptic and in Search window I have written "avant window navigator" search string. There are 13 packages shown up. If I want to make system as clean as possible which package should I uninstall? :(

If I understand correctly when installing new program there can be an upgrade of other packages already installed on system. So when uninstalling program, all packages can't be removed.

I think the behavour in Add/Remove when remove is executed on program should be:
1. uninstall any package that can be safely removed
2. leave any package that is dependent on some other software
3. when (or if) other the last program that is dependent on particular packages is uninstalled then all packages can be safe to remove.

---

### Post by abcuser on 2009-01-17
> **skern03 said:**
> you can post it as a bug on Launchpad
I tried to register Launchpad, so I entered e-mail address, and Launchpad return info that e-mail was sent to confirm registration. But there is no new mail in my inbox. :(

---

### Post by kranny on 2009-01-17
You have to use compiz or compiz-fusion for awn to work..So it might be showing shows it as a dependency.Its the other way round..(Backup ur compiz deb files from /var/apt/cache/archivesincase of a complete removal) and reinstall compiz fusion after uninstalling AWN

---

### Post by skern03 on 2009-01-17
> **abcuser said:**
> @skern03, sure I have checked Synaptic and in Search window I have written "avant window navigator" search string. There are 13 packages shown up. If I want to make system as clean as possible which package should I uninstall? :( 

You should locate the actual entry named Avant Window Navigator, and right-click on the entry. Select Mark for complete removal. It will then scan for dependencies and when it deletes the app, it will also delete config files.

---

### Post by abcuser on 2009-01-18
Hi,
"avant window navigator" or "Avant Window Navigator" is equal Synaptic is not case sensitive.

What I am afraid is when this string is written in Synaptic it also marks brltty package which in descriptions is written: "Access software for a blind person using a braille display". There are also other that looks they have nothing in common with AWN.

Regards

---

### Post by abcuser on 2009-01-18
> **kranny said:**
> You have to use compiz or compiz-fusion for awn to work..[B]Yes I know that. I have turn on Sytem | Preferences | Appearance | Visual Effects | Normal (Extra is not working at all). But it looks other thinks on my PC are not working as well, for example [Compiz turned on: openOffice menus not displayed](http://ubuntuforums.org/showthread.php?t=1006508)

---

### Post by Partyboi2 on 2009-01-18
> **abcuser said:**
> Hi,
"avant window navigator" or "Avant Window Navigator" is equal Synaptic is not case sensitive.

What I am afraid is when this string is written in Synaptic it also marks brltty package which in descriptions is written: "Access software for a blind person using a braille display". There are also other that looks they have nothing in common with AWN.

Regards
Can you uninstall awn then reinstall the packages that it removes?

---

### Post by skern03 on 2009-01-18
> **abcuser said:**
> Hi,
"avant window navigator" or "Avant Window Navigator" is equal Synaptic is not case sensitive.

What I am afraid is when this string is written in Synaptic it also marks brltty package which in descriptions is written: "Access software for a blind person using a braille display". There are also other that looks they have nothing in common with AWN.

Regards

The package manager is smart enough to know which packages are dependent upon AWN. 

I've attached an image that shows the package you need to uninstall. Its name is: avant-window-navigator.

---

### Post by abcuser on 2009-01-18
> **skern03 said:**
> Its name is: avant-window-navigator.
Hi,
I have done the following:
1. I have market as "completely remove" avant-window-navigator package. 
2. Then I removed all packaged labeled "auto removable.
3. Then I removed all packages labeled "residual config".
4. Search for "avant window navigator" and there was no packaged market as installed with this search string.

Just wondering why Ubuntu from Add/Remove could do what I have done. :-k

Thanks for help
Regards

---

### Post by abcuser on 2009-01-26
Hi,
I have filed idea to Branstorm. If you like idea please vote for it:
[http://brainstorm.ubuntu.com/idea/17664/](http://brainstorm.ubuntu.com/idea/17664/)
Regards

---

