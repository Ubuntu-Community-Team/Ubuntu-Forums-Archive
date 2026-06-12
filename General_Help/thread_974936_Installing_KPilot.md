---
title: "Installing KPilot?"
date: 2008-11-08
forum: General Help
---

### Post by iheartubuntu on 2008-11-08
For the life of me I cannot figure out how to install KPilot. I did it on my work computer no prob, but I cannot figure it out here at home. Any DEB files of KPilot? make things easier?

Thanks for the help!

---

### Post by jayjay960 on 2008-11-08
It sounds like you're using Kubuntu, but I think that must have a package manager like gnome. Open up Synaptic Package manager (On ubuntu it's System > Administration > Synaptic Package Manager) and do a search there.

---

### Post by iheartubuntu on 2008-11-08
Yes, at work Im pretty sure I used Synaptic and found "kpilot" right away and installed it. I use Ubuntu 8.10 at both home and work and I am unable to find it in synaptic at home.

---

### Post by iheartubuntu on 2008-11-08
* bump *

---

### Post by iheartubuntu on 2008-11-08
Just made it into work here. My Ubuntu 8.10 here shows KPilot in the Synaptic Package Manager.

KPilot 4:3.5.10-0

I dont know how it got into the package manager there. Its not available via the Add/Remove reps.

---

### Post by iheartubuntu on 2008-11-08
I wonder if it has something to do with the backports enabled in my software sources? I have them checkmarked here at home. Hmmmmmmm.

---

### Post by jimmyhacker on 2008-11-08
you can use adept for install synaptic manager or you need some repos for kpilot.kpilot comes with kde-base package.

---

### Post by maybeway36 on 2008-11-08
KPilot is in the universe repository. Make sure that's enabled, then press "Reload" on Synaptic and see if it shows up.

---

### Post by iheartubuntu on 2008-11-08
Thanks for the tip.

* mental note: do not try to find and install software in the middle of the night. :D

---

### Post by Who on 2008-11-19
Okay, so it _is_ late at night here, so I might just be missing things BUT. I _really_ don't think I have a kpilot package in Synaptic. I have Ubuntu installed, Universe enabled and I've reloaded my packages. If I search for kpilot I only get libpisock and korganizer show up!?

What am I doing wrong? Which repositories do I need enabled?

---

### Post by want-to-believe on 2008-11-23
I have the same problem I believe. I can't seem to locate kpilot. I am using adept, kde desktop 4.?.?, and I know that I at least saw it in previous versions of kde. I must confess that I have installed several versions of Ubuntu, and only experiment with my Palm on Ubuntu. I am forced by my boss to support Windows machines all day, and have to use Outlook while at work or he won't pay me!! Anyway, am very interested to learn any solution that you find. Thanks

---

### Post by iheartubuntu on 2008-11-24
anyone? bump

I cant figure out why I can find kpilot in synaptic on one computer, but not another.

---

### Post by iheartubuntu on 2008-12-11
try this again... anyone with any solutions? Kpilot is GREAT, I really like it a lot and it works fine on my work computer, but I would also like to use it at home. Im unable to install kpilot at home.


> **shirteesdotnet said:**
> anyone? bump

I cant figure out why I can find kpilot in synaptic on one computer, but not another.

---

### Post by want-to-believe on 2008-12-11
I have spent hours looking for it. No luck. I really like the kde desktop, kontact is great, but where is kpilot?

---

### Post by Harbard on 2008-12-22
Okay, I'll give it a shot. Please forgive me if I repeat anything.

Open the Synaptic package manager.  It's in the "System" menu.

Then, open settings->repositories.

Then, make sure all four boxes are checked and close the window.

Then, click on the "reload" button.

Then, click on the search button.  Type in kpilot.  You should get three results:  korganizer, kpilot, and libpisock9. Click on kpilot and mark it for installation, then click "apply changes".  relax for a minute or two, then you should be done.

---

### Post by iheartubuntu on 2008-12-23
Harbard! I wish it was this easy. All four boxes are checked off and when I type in "kpilot" I get these two options:

-libpisock9
-korganizer

with the first one installed already. Theres no option for kpilot to install and if I try to install kpilot from the command line (sudo apt-get install kpilot) I get this error here:

> 
[B]Package kpilot is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package kpilot has no installation candidate[/B]

Any ideas?

> **Harbard said:**
> Okay, I'll give it a shot. Please forgive me if I repeat anything.

Open the Synaptic package manager.  It's in the "System" menu.

Then, open settings->repositories.

Then, make sure all four boxes are checked and close the window.

Then, click on the "reload" button.

Then, click on the search button.  Type in kpilot.  You should get three results:  korganizer, kpilot, and libpisock9. Click on kpilot and mark it for installation, then click "apply changes".  relax for a minute or two, then you should be done.

---

### Post by Harbard on 2009-02-04
Ok...still no luck.  I upgrade to 8.10 because my Visor stopped syncing.  NOW I see your problem.  kpilot does not exist in any of the the repositorys for Intrepid Ibex.  As far as I can tell there is now way to sync your PDA anymore.

Anyone have any ideas?

---

### Post by iheartubuntu on 2009-02-05
> **Harbard said:**
> Ok...still no luck.  I upgrade to 8.10 because my Visor stopped syncing.  NOW I see your problem.  kpilot does not exist in any of the the repositorys for Intrepid Ibex.  As far as I can tell there is now way to sync your PDA anymore.

Anyone have any ideas?

Hmmmm... I think I understand your point. When I installed Kpilot on this computer at work, it was still 8.04, then upgraded to 8.10, and it still works. On my other two computers at home, they have fresh installs of 8.10 and I am unable to install kpilot.

Seems like we should file a bug somehow about this.

---

### Post by Harbard on 2009-02-13
Okay, I have since found some information that Kpilot is included in the package named "kdepim".  however, I still can not find how to start it as it does not show up in the menus.  I might have to go to the konsole to start it.

---

### Post by Harbard on 2009-02-13
As far as I can tell, kpilot is NOT included in the kdepim package...even though the documentation says it is.

---

### Post by Harbard on 2009-02-13
final update for me.  Seems like I'll have to revert back to 'Hardy Heron' or switch to another distro if I want to use my pda.  It will not work under Gnome or KDE, it WILL work under WindowsXP, and CentOS 5 (and other Fedora distros).  Trouble is, the machine with CentOS is my laptop.  I need it on my desktop...so I might just give up Ubuntu and switch to CentOS.

---

### Post by iheartubuntu on 2009-07-24
Just wanted to update this... kPilot comes with Jaunty (9.04) YAY!

---

