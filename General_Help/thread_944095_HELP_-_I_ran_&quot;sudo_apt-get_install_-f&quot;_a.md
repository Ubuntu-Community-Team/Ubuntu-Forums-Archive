---
title: "HELP - I ran &quot;sudo apt-get install -f&quot; and now everything is gone!"
date: 2008-10-11
forum: General Help
---

### Post by hatboysam on 2008-10-11
I know a fair bit about the workings of ubuntu and how to get things done but my knowledge of the effect of specific commands is little to none.
I was following a guide to get a sweet theme for Gnome and it recommended a "sudo apt-get install -f"
NOW EVERYTHING IS GONE
i noticed while the terminal was executing the command that it was removing a ton of stuff, but i figured it would put it all back.  WRONG.
So now my Ubuntu will not boot to a desktop, only to a very basic terminal.  How can I get my desktop/apps back?

If it matters i was on 7.10 Gutsy Gibbon

---

### Post by Yellow Pasque on 2008-10-11
```
sudo apt-get install ubuntu-desktop
```
If you want to see all of the packages that were installed (and have a handy way to reinstall all of your packages):
```
sudo cat /var/log/apt/term.log
```

---

### Post by bodhi.zazen on 2008-10-11
Try :

```
sudo apt-get install ubuntu-desktop
```

---

### Post by hatboysam on 2008-10-11
when i try "apt-get install ubuntu desktop"
I get a list of approx, 100000000000000 things that take the form of "Recommends: (app here) but it is not going to be installed"
things that go in (app here) include, but are not limited to: pidgen, openoffice,rhythmbox, etc

---

### Post by Yellow Pasque on 2008-10-11
You'll have to link us to the guide or figure out which package is causing the problem and uninstall it, because somewhere you installed a package that wasn't from the repo and/or meant for your distro, and that has everything screwed up.

---

### Post by bodhi.zazen on 2008-10-11
Any error message ?

Did you alter your sources ?

What did you install anyways ?

---

### Post by hatboysam on 2008-10-11
here is the guide: [http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23/](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23/)

I dont know as much as most of you but i'd say its not a package causing the problem but rather a lack of packages.  I think i removed every single package on my system.

---

### Post by Nxion on 2008-10-11
> **hatboysam said:**
> I know a fair bit about the workings of ubuntu and how to get things done but my knowledge of the effect of specific commands is little to none.
I was following a guide to get a sweet theme for Gnome and it recommended a "sudo apt-get install -f"
NOW EVERYTHING IS GONE
i noticed while the terminal was executing the command that it was removing a ton of stuff, but i figured it would put it all back.  WRONG.
So now my Ubuntu will not boot to a desktop, only to a very basic terminal.  How can I get my desktop/apps back?

If it matters i was on 7.10 Gutsy Gibbon


Thats strang that that happend. if it asked you to run 

```
sudo apt-get install -f
```

This was asking you to fix broken packages. Why it uninstall ed everything is a mystery. It was supposed to install adition stuff. Are you sure that you ran this command?

```
sudo apt-get install -f
```

Regaurds,
Nx

---

### Post by hatboysam on 2008-10-11
I am positive the exact command was "sudo apt-get install -f" because i just went into my terminal history and checked.
While the command was taking effect (this took like 15 minutes) the terminal showed a ton of things being removed.

Anyway, regardless of what happened, what do i do now?

---

### Post by Yellow Pasque on 2008-10-11
Note that the guide you followed was for Ubuntu Hardy, and you were running Ubuntu Gutsy.

Does this work?
```
sudo apt-get remove avant-window-navigator-trunk awn-manager-trunk awn-extras-applets-trunk
sudo apt-get install ubuntu-desktop
```

---

### Post by bodhi.zazen on 2008-10-11
How far did you get on that how-to ?

You will have to work backwards, remove any .deb you installed, and then restore your /etc/apt/sources.list

then

sudo apt-get update && sudo apt-get install ubuntu-desktop.

---

### Post by Nxion on 2008-10-11
> **hatboysam said:**
> here is the guide: [http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23/](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23/)

I dont know as much as most of you but i'd say its not a package causing the problem but rather a lack of packages.  I think i removed every single package on my system.

Can you try to post the results of this command?

```
 cat /var/log/auth.log
```

With the about command we can seee what commands were run because you asked the system for elevated privileges.

Its a idea :)

---

### Post by Nxion on 2008-10-11
> **Nxion said:**
> Can you try to post the results of this command?

```
 cat /var/log/auth.log
```With the about command we can seee what commands were run because you asked the system for elevated privileges.

Its a idea :)

Ingnore this post. I am slow, I didn't see your other posts. :|

---

### Post by hatboysam on 2008-10-11
I tried that command and the results were huge.
In response to how far i got in the guide, i got up until the point where it recommended that command (with success) but I skipped the part about AWN

---

### Post by hatboysam on 2008-10-11
> **bodhi.zazen said:**
> How far did you get on that how-to ?

You will have to work backwards, remove any .deb you installed, and then restore your /etc/apt/sources.list

then

sudo apt-get update && sudo apt-get install ubuntu-desktop.

how do i restore my sources list?
and also i didnt really install anything from that guide, just moved some theme packages around

---

### Post by hatboysam on 2008-10-11
OK sorry to triple post but it is 1AM here and i need sleep so if you guys could post a couple of things for me to try in the morning that would be great.

---

### Post by Yellow Pasque on 2008-10-11
You'll need to remove the heathen repos from your sources.list
```
sudo nano /etc/apt/sources.list
```
Delete the lines you added
```
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
```

---

### Post by Nxion on 2008-10-11
> **hatboysam said:**
> I tried that command and the results were huge.
In response to how far i got in the guide, i got up until the point where it recommended that command (with success) but I skipped the part about AWN


If I am not mistaked maybe this command was the reason everythiing went crazy.

"sudo dpkg -i –force-overwrite *.deb"

Sounds to me that this command alone for some reason destroyed the packages on the machine and when he ran "sudo apt-get install -f", since this command is ment to FIX broken packages, it saw them as broken and uninstalled  everything.

Am I mistaken bodhi_zazen?

---

### Post by hatboysam on 2008-10-11
Ok so i piped the results of "apt-get install ubuntu-desktop" through less and i got a huge list of things, some starting with "Depends:"  and some with "Reccomends:"
I wrote down all of the ones it depends on, should i manually install those?

---

### Post by Yellow Pasque on 2008-10-11
Just a thought... You might want to consider backing up your personal data and starting over fresh with Ubuntu Hardy LTS.

> I wrote down all of the ones it depends on, should i manually install those?
Why doesn't the ubuntu-desktop package install automatically? You could manually install packages, but you really should fix your repo situation or you could easily find yourself in this position again.

---

### Post by OutOfReach on 2008-10-11
Try:
```
sudo aptitude install ubuntu-desktop
```

Maybe that will install all the recommendations.

---

### Post by Yellow Pasque on 2008-10-11
> **Nxion said:**
> If I am not mistaked maybe this command was the reason everythiing went crazy.

"sudo dpkg -i –force-overwrite *.deb"

Sounds to me that this command alone for some reason destroyed the packages on the machine and when he ran "sudo apt-get install -f", since this command is ment to FIX broken packages, it saw them as broken and uninstalled  everything.

Am I mistaken bodhi_zazen?

One can uninstall all of their packages with *sudo apt-get install -f <package>* if the dependencies of the package aren't available (in this case, the .deb's control file was written with Hardy in mind, and the user had Gutsy repos).

---

### Post by hatboysam on 2008-10-11
At this point i have resigned to a complete reinstall (i do this about 2x a year after i f*** up my current install)

Thanks so much for the help you guys, I have never been in a forum quite so awesome.

---

### Post by koenn on 2008-10-11
> **Temüjin said:**
> One can uninstall all of their packages with *sudo apt-get install -f <package>* if the dependencies of the package aren't available (in this case, the .deb's control file was written with Hardy in mind, and the user had Gutsy repos).

yes, I reckon it's something like that - unresolvable dependencies or version conflicts that trigger removal of a number of packages when doing "fix everything", then the removal of other packages that depended on those, and so on. The dpkg force option also indicates something like that : it was probaly used to ignore warnings/errors about dependencies.

ubuntu-desktop will pobably be uninstallable because it, or one of the packages it will pull in as a dependency, would re-create the same dependency conflict(s).

The cure is what bodhi-zazen posted earlier :
remove all the packages installed in that 'leopard' howto,
remove the troublesome lines from apt sources list
install ubuntu desktop
never do this again unless you're aware of the consequences of playing with unsupported software, and are willing to deal with them.

---

### Post by Nxion on 2008-10-14
> **Temüjin said:**
> One can uninstall all of their packages with *sudo apt-get install -f <package>* if the dependencies of the package aren't available (in this case, the .deb's control file was written with Hardy in mind, and the user had Gutsy repos).


Gotcha, never thought of it that way. Thanks :)

---

