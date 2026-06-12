---
title: "complex problem with synaptec installing kubuntu"
date: 2008-08-26
forum: General Help
---

### Post by Fifoxtasy on 2008-08-26
hi everybody!

i'm pretty new to linux and ubuntu, so far everything worked out fine, and if not i found what i needed on the internet. but now i ran into a problem that is too complex for me. i searched these forums, without success. please help!

i installed ubuntu (8.04) on my sony laptop a while ago, and now i wanted to try the KDE interface. i read that i could just install it with the synaptic package manager - so i did. i got into synaptic chose: EDIT > mark packages by task...
a window opened and i selected kubuntu KDE4 desktop

while installing synaptic failed to download several packages, gave me an error message and i chose not to continue without all the packages. closed the program and just did the same thing again. it downloaded some more and then installed.

i restarted to get into the new shiny KDE.
trying to find my way around i get error messages everywhere. i get crashes. there seem to be some settings and programs missing. i can't login as root anymore and my user has less priveledges and i can't edit them any more. a lot of strange things going on. 
the applications launcher menu is a complete mess of gnome and kde programs, which i read on the forums should be expected when installing like this. but there are a lot of links in there that don't have an icon. and some that won't run.

could somebody please explain if some of these things are normal (supposed to happen when you install kubuntu packages in ubuntu)?

well, i tried to fix the problems by running synaptic again and reinstall the packages. but i can't select them the way i did before, so i search kubuntu and select to install the kubuntu-desktop package. synaptic tells me for other changes to be made, i click ok, i get an error message:
```
kubuntu-desktop:
 Depends: kde-guidance but it is not going to be installed
 Recommends: kde-guidance-powermanager but it is not going to be installed
```
when searching for the culprit package and trying to select it manually, it gives me some other packages, i follow it package after package. then in the end i find a package that (some python-dev, can't remember exact name [ask if it is important]. it says that it needs an older version of some python2.5 (something like that) package. i try to force it to use the older version - synaptic doesn't do anything.
removing broken packages doesn't help either.

i tried some stuff in the command line
```
sudo apt-get install -f
```
clean autoclean purge update autoremove

also: ```
sudo apt-get --purge remove synaptic
```
updating sources and reinstalling it
no success
```
~$ sudo dpkg --configure -a
```
nothing
```
sudo aptitude remove kubuntu-desktop
```
no packages are removed. do i need to run this from outside xwindow system?

tried some other stuff i read about on the forums which i can't remember anymore.
nothing i tried repaired the package manager, still have those broken packages.

i really don't know what to do.
please help

---

### Post by stoneybroke on 2008-08-26
Try entering sudo apt-get autoremove to remove broken packages.

---

### Post by Fifoxtasy on 2008-08-26
@stoneybroke: thank you for your quick response. i think i already tried that before.
i just tried again and it doesn't change anything. any other ideas?

---

### Post by Fifoxtasy on 2008-08-26
i just played around with aptitude. i cannot uninstall all the installed packages (remove kubuntu-desktop) because it is not installed (not completely i guess???). and i tried remove kubuntu-kde4-dekstop, which was removed + one dependency. so no real change there. at least aptitude can offers me a solution when i tell it to install kubuntu-desktop. it lists the broken python2.5 package and offers to revert to an earlier version. i didn't do it yet, because i don't want to install kde any more (i'm kind of pissed). and aptitude says it would have to download hundreds of MB again and i'm on a very slow and limited connection.
would it be worth trying? so i could maybe try to uninstall the package afterwards and go back to the ubuntu i had before?
or is there something else i need to do to get ubuntu back? i noticed that a lot of gnome programs are gone (gupdater...). what do i need to do to get them back? isn't there an easy and CLEAN way to switch between ubuntu & kubuntu?

---

### Post by stoneybroke on 2008-08-26
Hi to get back to the Ubuntu desktop you will have to select log out from the close down menu then when the log in screen appears click on options at the bottom left then select Ubuntu enter your username/password and it will bring you back to the Ubuntu desktop.

If you have Synaptic Package Manager go to the Edit>fix broken packages tab and use that to fix the packages.

I have tried KDE and KDE4 and personally I think KDE is a lot better than KDE4


Hope that helps

---

### Post by Fifoxtasy on 2008-08-27
i installed the kubuntu-desktop with the help of aptitude and it worked! aptitude is great, it did what no other package manager could do! now i can switch between GNOME, KDE, KDE4.

@stoneybroke: you are right KDE is way better than KDE4 its really amaying how this could get that much worse from in a later version. i hope they can clean up the mess they made soon.
before i fixed it with aptitude, i tried to fix broken packages in synaptic, but it didnt help. nothing happened.


but well the programs in the menu are still a big mix of gnome and kde apps, which makes it harder to compare the two. i still havent made my mind up which one to choose. but im not keeping both thats for sure.

i am still wondering if there would have been an easier way to fix the issue with the broken package than installing a whole bunch of others.

if i am going to uninstall one of the desktop envirements is it going to uninstall all the other programs as well? or will it be a complete mess?

---

