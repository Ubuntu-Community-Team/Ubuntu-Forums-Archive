---
title: "Getting an error when installing anything"
date: 2008-10-05
forum: General Help
---

### Post by DemonKyoto on 2008-10-05
Disclaimer: Linux noobie :P

It all started when I tried to install Wine, per:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

I did the following with no problem:
> Adding the WineHQ APT Repository:

First, open a terminal window (Applications->Accessories->Terminal). On Debian, you will need to open a root terminal. Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

For Ubuntu Hardy (8.04):
sudo wget [http://wine.budgetdedicated.com/apt/...t.d/hardy.list](http://wine.budgetdedicated.com/apt/...t.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list

Then update APT's package information by running 'sudo apt-get update'.

I then clicked on the link to apt://wine and tried to download it from the Add/Remove option, when I do so, I get this with both methods.

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report. 

So I entered "sudo dpkg --configure -a" and entered my password when prompted, at which point it launched the Moblock control configuration in the terminal ( I have Moblock installed of course, and disabled at the time trying all this ).

So my experiment with Wine ended, and now any time I try to use Add/Remove, it gives me that same dpkg error, as well as when I access some of the Administration tools. Can someone give me some ideas for how to get everything back to normal ( and get Wine installed, but thats secondary now compared to fixing the error ).

Thanks.

---

### Post by fooman on 2008-10-05
open a terminal and type or copy/paste the following:

```
sudo dpkg --configure -a
```

if that goes off without an error,  and you have already added the wine repository... then follow with these (one at a time):

```
sudo apt-get update

sudo apt-get install wine
```

edit: OOPS...didn't see that you already tried "sudo dpkg --configure -a" ...not familiar with "Moblock", sorry!

---

### Post by DemonKyoto on 2008-10-05
> **fooman said:**
> open a terminal and type or copy/paste the following:

```
sudo dpkg --configure -a
```

if that goes off without an error,  and you have already added the wine repository... then follow with these (one at a time):

```
sudo apt-get update

sudo apt-get install wine
```

edit: OOPS...didn't see that you already tried "sudo dpkg --configure -a" ...not familiar with "Moblock", sorry!

Sok, thanks for reminding me:

When entering commands like the above, I get the dkpg error after all of them as well.

---

### Post by nowshining on 2008-10-05
try again after:

```
sudo apt-get autoremove
```

Then try again after:

```
sudo apt-get autoclean
```

then try:
```

Sudo apt-get clean
```

then if u still have probs, try the dpkg -a or whatever it asked u to do..if all else fails try to logout and backin - if that fails - try a reboot...

---

### Post by DemonKyoto on 2008-10-05
> **nowshining said:**
> try again after:

```
sudo apt-get autoremove
```

Then try again after:

```
sudo apt-get autoclean
```

then try:
```

Sudo apt-get clean
```

then if u still have probs, try the dpkg -a or whatever it asked u to do..if all else fails try to logout and backin - if that fails - try a reboot...

I get the same error when I entered both the autoremove and autoclean commands, and it says the 3rd command doesnt exist.

Already have logged out and rebooted  before, no change.

---

### Post by nowshining on 2008-10-05
but did u reboot??

edit: for the 3rd command change the capistal S in sudo to a smaller one...

---

### Post by DemonKyoto on 2008-10-05
> **nowshining said:**
> but did u reboot??

edit: for the 3rd command change the capistal S in sudo to a smaller one...

As I said, yes, I rebooted, several times.

sudo apt-get clean didnt give me an error, just prompted me for my password, then went back to the basic prompt, but it didnt do anything, the other commands still give the same error, and still cant do anything in Add/Remove.

---

### Post by nowshining on 2008-10-05
srry mate :) didn't see u said u rebooted..hehe, apt-get clean removes all files in cache in the /var/cache/apt directory...

autoclean removes nolonger installed files, example if u installed lynx and then removed it autoclean should remove only the lynx package that u installed, etc..

now try the following two and if nothing happens - open up synaptic do u get any errors?

```
sudo apt-get -f install
```

The above command means force install any needed packages and fix any broken ones by of course forcing a install the following seems the same but it removes the packages  that are broken - hence if u do manual stuff and try to install anything in another distro, etc.. or another ubntu version via debs, it will May just hose ur system by removing or trying to remove everything...
```

sudo apt-get install -f
```

edit: by the way u are using Hardy 8.04 right??

---

### Post by DemonKyoto on 2008-10-05
No prob nowshining :) and yes, 8.04

Tried both of those, and still:

> demonweb@demonweb-desktop:~$ sudo apt-get -f install 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
demonweb@demonweb-desktop:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

When I open synaptic:
[IMG]http://www.demon-web.com/1.png[/IMG]

---

### Post by nowshining on 2008-10-05
so u tried rerunning dpkg --configure -a did u add a sudo in front on the command dpkg --configure -a ??

---

### Post by DemonKyoto on 2008-10-05
Yep. When typing it in I get this:
[IMG]http://www.demon-web.com/2.png[/IMG]
Which after a few seconds, turns into this:
[IMG]http://www.demon-web.com/3.png[/IMG]
But I also have Moblock disabled.

---

### Post by nowshining on 2008-10-05
remove the program moblock ```
sudo apt-get remove moblock --purge 
```

edit: or did u click ok, press the TAB key until ok is highlighted and then press enter on ur keyboard..u were looking at is a config screen for the program thru the CLI... :)

---

### Post by DemonKyoto on 2008-10-05
> demonweb@demonweb-desktop:~$ sudo apt-get remove moblock --purge
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
demonweb@demonweb-desktop:~$ 

:(

---

### Post by nowshining on 2008-10-05
see my edited post above...

---

### Post by DemonKyoto on 2008-10-05
Getting closer, didnt know how to hit the OK, but I got Moblock configured, now when I enter sudo dkpg --configure -a, I get:

> demonweb@demonweb-desktop:~$ sudo dkpg --configure -a
[sudo] password for demonweb: 
sudo: dkpg: command not found


---

### Post by taladan on 2008-10-05
dpkg not dkpg

tal

---

### Post by DemonKyoto on 2008-10-05
woot, got it all worked out now, thanks everyone

---

### Post by nowshining on 2008-10-06
glad u got it figured out :)

---

