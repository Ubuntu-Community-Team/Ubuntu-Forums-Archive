---
title: "Obtaining the MAC OS look..."
date: 2008-08-01
forum: General Help
---

### Post by PsychedelicWonders on 2008-08-01
I've been given these two links for a MAC OS...

Mac here:

[http://www.taimila.com/?q=node/11](http://www.taimila.com/?q=node/11)

and for ubuntu-specific, this one is good:

[http://rockmanx.wordpress.com/2008/0...c-hardy-heron/](http://rockmanx.wordpress.com/2008/0...c-hardy-heron/)


So what are the real differences between the guides on those two lists? 

I like the way the desktop looks in the 2nd link compared to the 1st one. (maybe its just the background pic and the rest is the same, I have no idea?)

thanks though.

---

### Post by lolobu on 2008-08-01
Well if you want your desktop to look like a Mac, both options will do the job. Both don't cover exactly the same items but you can do a mix. Just try each item one after the other and so if the results suits you.
All those themes, icons ... are added on the top of the current install. If you don't like it, you can always get back to the default Human Ubuntu theme.

---

### Post by overdrank on 2008-08-01
> **PsychedelicWonders said:**
> I've been given these two links for a MAC OS...

Mac here:

[http://www.taimila.com/?q=node/11](http://www.taimila.com/?q=node/11)

and for ubuntu-specific, this one is good:

[http://rockmanx.wordpress.com/2008/0...c-hardy-heron/](http://rockmanx.wordpress.com/2008/0...c-hardy-heron/)


So what are the real differences between the guides on those two lists? 

I like the way the desktop looks in the 2nd link compared to the 1st one. (maybe its just the background pic and the rest is the same, I have no idea?)

thanks though.

Hi and the seconded link is not found. :)

---

### Post by lolobu on 2008-08-01
I assume it's that one :
[http://rockmanx.wordpress.com/2008/06/02/make-your-linux-ubuntu-look-like-a-mac-hardy-heron/]("http://rockmanx.wordpress.com/2008/06/02/make-your-linux-ubuntu-look-like-a-mac-hardy-heron/")

---

### Post by PsychedelicWonders on 2008-08-01
> **lolobu said:**
> Well if you want your desktop to look like a Mac, both options will do the job. Both don't cover exactly the same items but you can do a mix. Just try each item one after the other and so if the results suits you.
All those themes, icons ... are added on the top of the current install. If you don't like it, you can always get back to the default Human Ubuntu theme.

How do I tell exactly what items one has vs. the other so I can possibly do a process of elimination?

what would be considered "items"?

---

### Post by lolobu on 2008-08-01
Well if you read what's written in both articles, they exclain with a bit of details what's done in each section of the article. What I mean by item is a section, a section, whatever you call it, from the article.
In the second link they first talk about "Installing Cursor , GTK and Icon Theme" and so on. Just try what sounds interesting if if you don't get what it means, try anyway and you will see by yourself.

---

### Post by PsychedelicWonders on 2008-08-09
alright, I went with this walkthough...

[http://rockmanx.wordpress.com/2008/06/02/make-your-linux-ubuntu-look-like-a-mac-hardy-heron/](http://rockmanx.wordpress.com/2008/06/02/make-your-linux-ubuntu-look-like-a-mac-hardy-heron/)

I'm currently stuck on a couple of things for obtaining this...

First off in this step....

After completing above step , you can customize compiz by going to System > Preferences > Advanced Desktop Effects Settings .

1) I do not have an advanced desktop effects settings tab?

To install AWN you need to add extra repositories, now adding any additional repository carries certain amount of risk of screwing up your system so follow these step at your own risk :

To add repository :

echo &#8220;deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main&#8221; | sudo tee -a /etc/apt/sources.list
and

echo &#8220;deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main&#8221; | sudo tee -a /etc/apt/sources.list

After issuing above command type the following command to update your repositories :

sudo apt-get update

anf finally to install AWN issue the following command in the terminal window :

sudo apt-get install awn-manager-trunk awn-extras-applets-trunk

Now after completing above mentioned steps AWN should be properly installed , To Launch AWN go to (Applications -> Accessories -> Avant Window Navigator )

Is the "repository" the terminal?  there fore I just copy and past each step one by one into the terminal?

---

### Post by the real omni on 2008-08-09
> **PsychedelicWonders said:**
> 1) I do not have an advanced desktop effects settings tab?

Open Synaptic Package Manager (System -> Administration -> Synaptic). Once it's open, click 'Search' and look for 'compiz'

One of the listings will be called compizconfig-settings-manager or compiz-settings-manager. Mark that one for installation then click 'Apply'. 

Once the installation has finished you should be able to go to System -> Preferences -> Advanced Dekstop Effects (or something like that - sorry my ubu partition is unbootable right now so I'm going on memory)

> **PsychedelicWonders said:**
> Is the "repository" the terminal?  there fore I just copy and past each step one by one into the terminal?

You bet. Well, kinda, anyway. The 'repository' is not actually the terminal, but the terminal is where you paste the commands. 

NOTE: To paste into a terminal window use CTRL+SHIFT+V instead of the usual CTRL+V

The repository is an online server that maintains a database of available software packages. There's a main repository for Edgy and for Hardy but there is some 3rd-party software that hasn't made it through the full testing and verification process yet (not because they're lacking in stability but usually just because the people who do the verification have such a backlog) and to have the 3rd-party software show up in the list of available downloads, the 3rd-party repository has to be added so Synaptic can see the software package.

---

### Post by the real omni on 2008-08-09
One other note on Avant Window Navigator.

DO NOT download and install the regular version or the BZR version. Both versions are missing the extra-applets package and as such have very limited functionality. (Basically you can only use them as a taskbar/quicklaunch, but with the extra applets you can have allll kinds of nifty gizmo's)

To get the extra-applets pack you have to install the 'trunk' version of AWN instead.

NOTE: The 'trunk' version seems to have a bug that prevents the 'refresh' button from working in the AWN manager. This means once you've done your configuration you'll have to close and re-launch AWN in order to see the changes reflected. Personally I think this is a worthwhile trade-off in order to get all the awesome applets working.
NOTE2: If you use the system tray applet you'll have to log out and log back in instead of just closing and re-opening awn. Something to do with how gnome handles tray icons.

To install the 'trunk' version of AWN, see this guide:
[http://www.ventanazul.com/webzine/tutorials/avant-window-navigator-ubuntu](http://www.ventanazul.com/webzine/tutorials/avant-window-navigator-ubuntu)

It basically has the same AWN-related info and instructions as the guide you're using but it replaces the normal repositories with the trunk repositories and the normal packages with the trunk packages.

EDIT: Actually I think the BZR version does have the extra-applets package. I just wasn't able to get the BZR version to work in a stable fashion on Ubuntu 8.04 Hardy. You could try that out if the trunk version doesn't work.

Also if both the 'trunk' version and the 'bzr' version let you down, I'd recommend upgrading to Ubuntu 8.04 and trying with the more recent system.

---

### Post by PsychedelicWonders on 2008-08-09
alright got the first part, thanks.

Now I can just add or remove the desktop effects with no ill effects as I find fitting correct?

So now onto the second part....

so I go into terminal and paste these one by one, hit enter, let it install, and then paste the next one until I've completed the list?

echo &#8220;deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main&#8221; | sudo tee -a /etc/apt/sources.list

then after full install...

echo &#8220;deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main&#8221; | sudo tee -a /etc/apt/sources.list

correct?

One at a time?

and I can just copy and paste in the terminal... seems easy enough.  

But youre saying windows is ctrl+v where ubuntu is ctrl+****+v?

---

### Post by SunnyRabbiera on 2008-08-09
> **PsychedelicWonders said:**
> alright got the first part, thanks.

Now I can just add or remove the desktop effects with no ill effects as I find fitting correct?

So now onto the second part....

so I go into terminal and paste these one by one, hit enter, let it install, and then paste the next one until I've completed the list?

echo “deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main” | sudo tee -a /etc/apt/sources.list

then after full install...

echo “deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main” | sudo tee -a /etc/apt/sources.list

correct?

One at a time?

and I can just copy and paste in the terminal... seems easy enough.  

But youre saying windows is ctrl+v where ubuntu is ctrl+****+v?

you really dont need ctrl-shift-v to paste, its just a matter of right clicking and selecting "paste"

---

### Post by PsychedelicWonders on 2008-08-09
> **the real omni said:**
> One other note on Avant Window Navigator.

DO NOT download and install the regular version or the BZR version. Both versions are missing the extra-applets package and as such have very limited functionality. (Basically you can only use them as a taskbar/quicklaunch, but with the extra applets you can have allll kinds of nifty gizmo's)

To get the extra-applets pack you have to install the 'trunk' version of AWN instead.

NOTE: The 'trunk' version seems to have a bug that prevents the 'refresh' button from working in the AWN manager. This means once you've done your configuration you'll have to close and re-launch AWN in order to see the changes reflected. Personally I think this is a worthwhile trade-off in order to get all the awesome applets working.
NOTE2: If you use the system tray applet you'll have to log out and log back in instead of just closing and re-opening awn. Something to do with how gnome handles tray icons.

To install the 'trunk' version of AWN, see this guide:
[http://www.ventanazul.com/webzine/tutorials/avant-window-navigator-ubuntu](http://www.ventanazul.com/webzine/tutorials/avant-window-navigator-ubuntu)

It basically has the same AWN-related info and instructions as the guide you're using but it replaces the normal repositories with the trunk repositories and the normal packages with the trunk packages.

EDIT: Actually I think the BZR version does have the extra-applets package. I just wasn't able to get the BZR version to work in a stable fashion on Ubuntu 8.04 Hardy. You could try that out if the trunk version doesn't work.

Also if both the 'trunk' version and the 'bzr' version let you down, I'd recommend upgrading to Ubuntu 8.04 and trying with the more recent system.

so now youre saying the BZR version is the way to go and has no bugs but all the extras?

is the bzr version the one in my current walk through?

Or do I have to find it some where else?

i was on track... but now you confused me.  :)

---

### Post by the real omni on 2008-08-09
> **PsychedelicWonders said:**
> Now I can just add or remove the desktop effects with no ill effects as I find fitting correct?

You bet. I recommend taking the time to try out each and every desktop effect - some of them will surprize you! (Note - the Desktop Cube effect needs the Rotate Cube effect enabled in order to really make it worthwhile but oooohhhh mama is it ever worthwhile!! [example here](http://www.youtube.com/watch?v=dlhD_4pK4MM&feature=related))

> So now onto the second part....

so I go into terminal and paste these one by one, hit enter, let it install, and then paste the next one until I've completed the list?

echo &#8220;deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main&#8221; | sudo tee -a /etc/apt/sources.list

then after full install...

echo &#8220;deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main&#8221; | sudo tee -a /etc/apt/sources.list

correct?

One at a time?


Correct. :)

> 
But youre saying windows is ctrl+v where ubuntu is ctrl+****+v?

Not exactly, no. In almost every situation in Ubuntu, CTRL+V is the shortcut to paste, just like in winblows. 

In a terminal window, however, the command-line interface uses CTRL+V for something else (likewise with CTRL+C, which is used to cut short a command that's running.) As such, in order to paste into a terminal window you just press CTRL+SHIFT+V

---

### Post by PsychedelicWonders on 2008-08-09
> **the real omni said:**
> You bet. I recommend taking the time to try out each and every desktop effect - some of them will surprize you! (Note - the Desktop Cube effect needs the Rotate Cube effect enabled in order to really make it worthwhile but oooohhhh mama is it ever worthwhile!!)



Correct. :)



Not exactly, no. In almost every situation in Ubuntu, CTRL+V is the shortcut to paste, just like in winblows. 

In a terminal window, however, the command-line interface uses CTRL+V for something else (likewise with CTRL+C, which is used to cut short a command that's running.) As such, in order to paste into a terminal window you just press CTRL+SHIFT+V


i wanted to try out that cube thing... i dont even know what it does, but when i tried to enable cube desktop i get this message...

Plugin Desktop Wall provides feature largedesktop which is also provided by Desktop Cube

then it asks me to disable wall or cancel desktop cube... should I disable wall... will that affect anything else?

---

### Post by PsychedelicWonders on 2008-08-09
so do I have to do that trunk version you mentioned, or do I just continue to go through the walkthrough as he describes?

sorry, you confused me with this situation

---

### Post by PsychedelicWonders on 2008-08-09
what am I doing wrong....?

psychedelicwonders@JohnnyScience:~$ echo &#8220;deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main&#8221; | sudo tee -a /etc/apt/sources.list
[sudo] password for psychedelicwonders: 
&#8220;deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main&#8221;
psychedelicwonders@JohnnyScience:~$ echo &#8220;deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main&#8221; | sudo tee -a /etc/apt/sources.list
&#8220;deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main&#8221;
psychedelicwonders@JohnnyScience:~$ echo &#8220;deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main&#8221; | sudo tee -a /etc/apt/sources.list
&#8220;deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main&#8221;
psychedelicwonders@JohnnyScience:~$ sudo apt-get update
E: Type '&#8220;deb' is not known on line 56 in source list /etc/apt/sources.list
psychedelicwonders@JohnnyScience:~$

I pasted this exactly...

echo &#8220;deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main&#8221; | sudo tee -a /etc/apt/sources.list

echo &#8220;deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main&#8221; | sudo tee -a /etc/apt/sources.list

sudo apt-get update



And the final step the walkthrough wants me to do that I did NOT do yet, is

sudo apt-get install awn-manager-trunk awn-extras-applets-trunk

Is this the "Trunk" version you were suggesting for me to download?

That is straight out of the walk thru... so the walk thru is correct then?

---

### Post by PsychedelicWonders on 2008-08-09
still cant figure this out... any ideas why i was getting the error message?

---

### Post by PsychedelicWonders on 2008-08-09
anyone have any ideas what im doing wrong?

---

### Post by the real omni on 2008-08-09
Hi, sorry - didn't mean to confuse you.

The BZR version didn't work with my Ubuntu 8.04 system so I installed the trunk version. It has the refresh bug but that's pretty much the only bug I've found in the trunk version.

My understanding is you need the trunk version of libawn and the trunk version of awn-manager in order to use the trunk version of the extra-applets plugin.

My recommendation is to follow the walkthrough you're using for every step EXCEPT the AWN-related steps. For those steps, refer to the walkthrough I provided the link for, then once the trunk version of AWN is installed, go back to the other walkthrough to complete the other steps.

As for the warning for the desktop cube, yes - there will be a few compiz effects that conflict with each other because they try to handle the same tasks and step on each other's toes. As such, in order to enable some effects it requires others to be disabled.

Basically it all comes down to which effect you'd prefer to have handle that task. In my opinion - which is always right ;) - the Desktop Cube outshines the Large Desktop or Desktop Wall or whatever it is that gets disabled.

---

### Post by PsychedelicWonders on 2008-08-09
echo &#8220;deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main&#8221; | sudo tee -a /etc/apt/sources.list
and

echo &#8220;deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main&#8221; | sudo tee -a /etc/apt/sources.list

After issuing above command type the following command to update your repositories :

sudo apt-get update

anf finally to install AWN issue the following command in the terminal window :

sudo apt-get install awn-manager-trunk awn-extras-applets-trunk



so dont use ANY of that part of the walk through?

Your walk through takes care of all of those steps?

or do I still need to do the first 3 steps from his walk through?

---

### Post by PsychedelicWonders on 2008-08-09
do i want to install the short version or the long version for the following walkthru...

[http://www.ventanazul.com/webzine/tutorials/avant-window-navigator-ubuntu](http://www.ventanazul.com/webzine/tutorials/avant-window-navigator-ubuntu)

?

if i choose the long way, when I vist the archive do I download files or do I just copy and paste something in the terminal?

---

### Post by PsychedelicWonders on 2008-08-09
still stuck on the last post...

---

### Post by ad_267 on 2008-08-10
The long version.

The short version won't get you all the stuff you need.

Where it says:
```
# awn
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
```

You have to edit the file /etc/apt/sources.list and add these lines.
Ie: "gksu gedit /etc/apt/sources.list"

You can also add these by going to System - Administration - Synaptic Package manager and adding them to the repositories.

---

### Post by PsychedelicWonders on 2008-08-10
#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main

so that was my list....

and now i just paste 

gksu gedit /etc/apt/sources.list

to the very bottom and save?

what do I do then?

---

### Post by ad_267 on 2008-08-10
> **PsychedelicWonders said:**
> 
so that was my list....

and now i just paste 

gksu gedit /etc/apt/sources.list

to the very bottom and save?

what do I do then?

No.

You paste in: 
```
# awn
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
```
at the bottom and save.

The "gksu gedit /etc/apt/sources.list" command is needed to edit it as root so that you have permissions to save it. Then you do steps four and five by entering those commands in the terminal.

---

### Post by PsychedelicWonders on 2008-08-10
> **ad_267 said:**
> No.

You pasted in: 
```
# awn
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
```
at the bottom and save.

Are you telling me or asking me?

I havent done anything with what you told me, I have been doing a walkthru all day, so whatever is there is from the other steps I have taken.

What exactly do I do next?

The "gksu gedit /etc/apt/sources.list" command is needed to edit it as root so that you have permissions to save it. Then you do steps four and five by entering those commands in the terminal.[/QUOTE]

I just type in sudo gedit /etc/apt/sources.list and can edit and save the list no problem.

What does the gksu do instead of sudo?

I'm honestly just confused as to what to do next.

---

### Post by ad_267 on 2008-08-10
Sorry, that should have been "paste," not "pasted." gksu does the same thing except it's recommended to use gksu instead of sudo for graphical applications.

So just paste in those three lines and save the file.

---

### Post by PsychedelicWonders on 2008-08-10
but it seems those two main lines are already listed at the bottom of my list?

do i just have to put #awn above them to make them active or something?

I had a problem just a little bit ago with those particular lines being duplicated at the bottom of my list and was giving me install errors.

I have since removed the duplicates.

So I just add the #awn, or do I have to add duplicates again?... in which case, wont I get install errors again when trying other applications?

---

### Post by ad_267 on 2008-08-10
Sorry I didn't see that. Yes those lines are already there. So just keep going from step 4.

---

### Post by PsychedelicWonders on 2008-08-10
alright, finally i got it!

thanks everyone for the help.

Now what if i need to access the rest of the menu that used to be at the top?  how do I do that?

How do I shutdown/restart?

Is there any time and date icon that I can get to place on the dock?

here it is...

---

### Post by PsychedelicWonders on 2008-08-10
thats weird, I logged out and logged back in to make sure the changes took... and it went back to the old way again... but this time had the dock, but then I pressed the "current workstation" buttons at the bottom right and now the dock is gone?

---

### Post by ad_267 on 2008-08-10
> **PsychedelicWonders said:**
> alright, finally i got it!

thanks everyone for the help.

Now what if i need to access the rest of the menu that used to be at the top?  how do I do that?

How do I shutdown/restart?

Is there any time and date icon that I can get to place on the dock?

here it is...

You can add a menu and shutdown buttons etc to the dock by right clicking on an empty space on it select Dock Preferences and add plugins. I think there should be a clock.

---

### Post by PsychedelicWonders on 2008-08-10
why did my system go back to normal when i logged out and back in?

it seems i still have the dock... but all of the icons i previously dragged and dropped on there are no longer there... whats up with that?

---

### Post by PsychedelicWonders on 2008-08-10
this dock seems to work when it wants.

sometimes its there, sometimes its not.

now its not.

---

### Post by the real omni on 2008-08-10
> **PsychedelicWonders said:**
> why did my system go back to normal when i logged out and back in?

it seems i still have the dock... but all of the icons i previously dragged and dropped on there are no longer there... whats up with that?

That's strange behavior - I'd recommend starting a new thread titled "Avant Window Navigator icons disappear on log-out/in" or something to that effect.

---

### Post by PsychedelicWonders on 2008-08-11
Do you think the download I did had a bug in it?

Or is this that docking bug you were talking about before?

Do I have to restart this dock everytime I log in and out of ubuntu?

---

### Post by the real omni on 2008-08-11
> Do you think the download I did had a bug in it?

Or is this that docking bug you were talking about before?

It's probably related to the refresh bug I was talking about before. The bug I'm referring to is present when using the AWN Manager, not dragging-and-dropping icons onto the dock. 

It could be that the refresh bug impairs drag-and-drop functionality as well.

You could try adding the icons using the AWN manager instead... Right-click on the dock or any icon on the dock and the top option in context menu should be "Dock Preferences" - this launches the AWN Manager.

In the AWN manager, go to Launchers and add whatever launchers you'd like. The AWN manager is also how you add all the nifty applets that make the trunk version so much better than the other versions.

When you're done adding everything you want to add, log out and log back in. 

Theoretically all the icons you set up in the AWN manager should still be present when you log back in.

> Do I have to restart this dock everytime I log in and out of ubuntu? 

Two different ways to auto-start AWN on login:

Method 1) One of the options in the AWN manager, in the General section, is "Automatically start AWN on login". If you enable that option by selecting the check-box, AWN should load itself every time you log in.

Method 2) Another way to have AWN auto-start on login is to go to System -> Preferences -> Sessions and in the Session Preferences window that pops up, add an entry with the command:
```
avant-window-navigator
```

NOTE: Use _either_ method 1 _**OR**_ method 2, _not both_. (ie, if Method 1 doesn't work, try Method 2, but you don't need to do both if the first one works.)

---

### Post by PsychedelicWonders on 2008-08-12
Hey I think option 1 is the one not working, I wanted to try option 2, but only got this far....



What do I put in the rest of the fields?

---

### Post by PsychedelicWonders on 2008-08-12
> **the real omni said:**
> 
You could try adding the icons using the AWN manager instead... Right-click on the dock or any icon on the dock and the top option in context menu should be "Dock Preferences" - this launches the AWN Manager.

In the AWN manager, go to Launchers and add whatever launchers you'd like. The AWN manager is also how you add all the nifty applets that make the trunk version so much better than the other versions.

Alright, dragging and dropping def freezes the dock for some reason which sucks.  Its so much easier.  Is there any way to fix this?

I can get to the Launcher screen, but what do I do from there?

What exactly are those gear looking icons already in there and why dont the rest of the icons I have show up in that list?

see the 2nd screen shot and look at the dock...

What exactly are "applets" and what do they do?

Also it seems that when I delete the shortcut on my desktop, it also seems to delete the shortcut on the dock?

Isnt that the point of the dock, to keep the desktop as clean as possible?

This thing seems to crash a lot.  Any ideas on that?

Should I remove this version that i installed and try perhaps another version?

Even when I manually turn it on, it doesnt seem to work all the time.

I have the setting to where the dock "disappears" below until you scroll your mouse over it.

It works from time to time.

---

### Post by the real omni on 2008-08-13
> **PsychedelicWonders said:**
> Hey I think option 1 is the one not working, I wanted to try option 2, but only got this far....



What do I put in the rest of the fields?

In the session preferences, you can put whatever you want for the "name" header, put "avant-window-navigator" for the command, and you can leave the description blank.

Likewise for configuring a launcher within the AWN manager.


As for the other bugs listed, I'm afraid I can't really help you. Maybe try a new thread with the title "Avant Window Navigator icons disappear when desktop icons deleted" or something to that effect.

---

### Post by PsychedelicWonders on 2008-08-14
alright it seems to be working smoother via sessions.  thanks.

But now what about these tool bars at the top and at the bottom... I like them and you need them, but I dont want to see them as I am going for the super clean look of MAC.

So what can I do to either turn these tool bars into something more attractive, or make them disappear until I scroll my mouse over them when I need them.

Ideally I'd like to do both of those ideas, or hear variations of both.

thanks.

---

### Post by the real omni on 2008-08-14
> **PsychedelicWonders said:**
> alright it seems to be working smoother via sessions.  thanks.

But now what about these tool bars at the top and at the bottom... I like them and you need them, but I dont want to see them as I am going for the super clean look of MAC.

So what can I do to either turn these tool bars into something more attractive, or make them disappear until I scroll my mouse over them when I need them.

Ideally I'd like to do both of those ideas, or hear variations of both.

thanks.

My suggestion would be to set it so it's not expanded and anchor it in the bottom-right corner of the screen.

You can right-click on the bottom task bar and delete it altogether - AWN replaces all the functionality of the bottom bar.

To resize the top bar and anchor it in the bottom right, see my guide here:
[http://ubuntuforums.org/showthread.php?t=885232](http://ubuntuforums.org/showthread.php?t=885232)

---

### Post by PsychedelicWonders on 2008-08-14
alright I will go through that guide, thanks.

I'm trying to drag the trash icon onto the desktop so I can then drag it on my dock... but its not moving.

Is there another way to get a trash icon?

Is there any way to modify the tool bars to be more appeasing to the eye?  Say in either a round, vista way, or whatever a MAC look would give to it?

Right now they are bland and basic like windows 3.4 or something really old school.

---

### Post by the real omni on 2008-08-14
> **PsychedelicWonders said:**
> 
I'm trying to drag the trash icon onto the desktop so I can then drag it on my dock... but its not moving.

Is there another way to get a trash icon?

In the AWN manager, select the "Applets" section. Scroll down the list and close to the bottom is the Trash applet. :)

To get an icon on your desktop as well, see this guide:
[http://www.howtogeek.com/howto/ubuntu/add-the-trash-can-icon-to-your-ubuntu-desktop/](http://www.howtogeek.com/howto/ubuntu/add-the-trash-can-icon-to-your-ubuntu-desktop/)

> Is there any way to modify the tool bars to be more appeasing to the eye?  Say in either a round, vista way, or whatever a MAC look would give to it?

Not sure but any time I have something I'm not sure about, google is my friend. :) Try googling terms like
```
ubuntu how to change panel theme
```

In general the combination of google and the ubuntu forums search can lead you to solutions in almost every case, you just have to be specific about your search terms.

---

### Post by overdrank on 2008-08-14
Moved :)

---

### Post by PsychedelicWonders on 2008-08-27
I am going to be removing 64 and applying 32.

Mainly for java,

But do you think this will help this dock bug I seem to have?

Should I still install the same dock package that was given to me in this thread?

Or is there a better one out there with no bugs?

Problems were:

Can't drag and drop icons onto dock

Dock seems to disappear after a few minutes.

---

### Post by PsychedelicWonders on 2008-08-29
bump

---

### Post by Crafty Kisses on 2008-08-29
Thanks for the links people, I appreciate it. :)

---

### Post by overdrank on 2008-08-29
> **PsychedelicWonders said:**
> I am going to be removing 64 and applying 32.

Mainly for java,

But do you think this will help this dock bug I seem to have?

Should I still install the same dock package that was given to me in this thread?

Or is there a better one out there with no bugs?

Problems were:

Can't drag and drop icons onto dock

Dock seems to disappear after a few minutes.

Hi and I am using 64 bit and AWN and have no issues with the dock.

---

### Post by PsychedelicWonders on 2008-08-29
What version did you install?

perhaps I should delete the version I have and try another version?

ideas on how to go about deleting it off of Ubuntu?

---

### Post by the real omni on 2008-09-28
Update:

There's been an update released for the -trunk version of AWN which fixes the refresh bug. 

Now there's no reason at all to use anything but the -trunk version! :)

---

### Post by lian1238 on 2008-09-28
Hi guys, there's a new cairo-dock which looks exactly (or almost) like Mac OSX! Lookie [_here_]("http://ubuntuforums.org/showthread.php?t=932649") (internal).

---

