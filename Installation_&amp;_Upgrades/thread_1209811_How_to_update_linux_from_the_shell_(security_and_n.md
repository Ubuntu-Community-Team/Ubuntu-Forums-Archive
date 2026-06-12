---
title: "How to update linux from the shell? (security and normal updates)"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by mario_man on 2009-07-10
Hi there,

how do I update Linux (Debian) from the shell? I know
```
sudo apt-get upgrade
sudo apt-get update
```but this tells me everything is up to date. Another Ubuntu however has some security fixes every some days. So I don't trust that the first system is properly up to date.

How do I update correctly?

Best, Mario

---

### Post by raymondh on 2009-07-10
Hi Mario_Man,

You could go to SOFTWARE SOURCES (system > administration).  In there, go to UPDATES tab and set updating to your preference (Automatic Updates).

I do hope I understood your question.

---

### Post by kerry_s on 2009-07-10
> **mario_man said:**
> Hi there,

how do I update Linux (Debian) from the shell? I know
```
sudo apt-get upgrade
sudo apt-get update
```but this tells me everything is up to date. Another Ubuntu however has some security fixes every some days. So I don't trust that the first system is properly up to date.

How do I update correctly?

Best, Mario


i'm confused is this debian compared to ubuntu or 1 ubuntu compared to another ubuntu?

the commands are right, you do the update first, then the upgrade.
if all else fails use synaptic, you can't go wrong in the gui.

---

### Post by jdackle on 2009-07-10
> **kerry_s said:**
> i'm confused is this debian compared to ubuntu or 1 ubuntu compared to another ubuntu?

the commands are right, you do the update first, then the upgrade.
if all else fails use synaptic, you can't go wrong in the gui.

The commads ORDER is actually WRONG!
*sudo apt-get upgrade* upgrades the packages based on the CURRENT package-list.
*sudo apt-get update* updates the PACKAGE-LIST. Only then the list of new packages to update becomes available.
Hence, the CORRECT ORDER is:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

HOWEVER, when using the INCORRECT order a second time, the list of new upgrades WAS made available. Hence, those should now be installed.
Was I clear on this one?

THEN... Debian is NOT Ubuntu!
They are two different distros maintained (and updated) by different people (who may take on a new update from the up-stream developpers of some package or not, as well as they can update the customisation to some package the original developpers didn't update themselves).
This said, Ubuntu is BASED ON Debian and most security updates Ubuntu provides for Ubuntu installs actually come from Debian (ONE upstream provider for Ubuntu).

FURTHERMORE, Debian itself has several different releases which are NOT all updated at the same time!
For the three Debian releases, see: [http://en.wikipedia.org/wiki/Debian#Distributions](http://en.wikipedia.org/wiki/Debian#Distributions)


So, all in all, this to say the fact your Ubuntu got updated and your Debian didn't, doesn't mean there is something wrong in the update procedures you are using (though there was, as stated above regarding the order of commands).

If indeed you realise your Ubuntu is providing you with updates that come from Debian (you can see where they come from when using the GUI Update Manager) which Debian isn't AND that the previous version of the package that was in Ubuntu is the same as the one in Debian, then there may be some actual technical problem, which most probably will be corrected by checking and correcting your */etc/apt/sources.list*).
In this case, you'd better be posting this to the Debian forums as they should help you better with the software sources (*aka* "repositories") for your Debian distro.

---

### Post by kerry_s on 2009-07-10
:lolflag: we've been schooled.

---

### Post by jdackle on 2009-07-10
> **kerry_s said:**
> :lolflag: we've been schooled.

I know you had, and I actually have some memory of myself getting happily shcooled by you on some other issue, Kerry. :P
I just wanted to make sure mario_man understood the correct order in which to invoke these commands. And all the rest. ;)

---

### Post by kerry_s on 2009-07-10
> **jdackle said:**
> I know you had, and I actually have some memory of myself getting happily shcooled by you on some other issue, Kerry. :P
I just wanted to make sure mario_man understood the correct order in which to invoke these commands. And all the rest. ;)

you have done well, very well. i am so proud to have witnessed the birth of the next master. ):P

yeah, i know i been getting lazier these days. i now tend to let the small things slide more & more. #-o

---

### Post by soho2014 on 2009-07-11
I might add, that you can join the 2 commands into 1 compound command:

sudo apt-get update && sudo apt-get upgrade

it's a tiny bit faster to get to the end result.

---

### Post by jdackle on 2009-07-11
> **kerry_s said:**
> you have done well, very well. i am so proud to have witnessed the birth of the next master. ):P

yeah, i know i been getting lazier these days. i now tend to let the small things slide more & more. #-o

:lolflag:
I'm lazier. I only come out with these flashes of mastery on a very sporadic basis.
:lolflag:

---

### Post by kerry_s on 2009-07-11
> **soho2014 said:**
> I might add, that you can join the 2 commands into 1 compound command:

sudo apt-get update && sudo apt-get upgrade

it's a tiny bit faster to get to the end result.

or just go all out & alias it. i simply type "u" to do both of those. ;)

---

### Post by mario_man on 2009-07-11
Thank you everybody.
To clarify:

I meant a Debian Etch installation which serves as server and thus has no GUI to use the update mechanisms there.

I did these update/upgrade commands (in both orders to make sure :-)) but there doesn't seem to be some update. When I compare this to my Ubuntu desktop installation, it's a bit amazing because there are several updates a week, usually.

But if you say that this is all fine, than I'm fine with it, too.

Many thanks, mario

---

### Post by kerry_s on 2009-07-11
etch! etch is old the current stable is lenny.
you need to change your sources.list to point to lenny or stable.
so **su** to root if your not root already:
**nano /etc/apt/sources.list**
change all "**etch**" to "**stable**"
then do the **update** & **upgrade**

stable is exactly that stable, they only do security updates mainly so don't expect many updates once you've upgraded to the latest stable(lenny). the reason i'm telling you to change it to "stable" instead of "lenny" is so you don't have to worry about it after that, you will automatically always run the latest stable.

i use debian testing(squeeze) on my systems.

---

### Post by mario_man on 2009-07-14
Thanks, this works and the machine updated a bunch of stuff. Unfortunately, this destroyed my mysql configuration.
But hopefully, I will find out, how to repair it.

```
mysql-server --configure
```

or so

mario

---

