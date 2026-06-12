---
title: "Changing the gdm theme? (9.10)"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by scottpledger on 2009-11-02
How does one change the gdm theme in 9.10?

---

### Post by mikerobinson on 2009-11-04
The Ubuntu developers made the executive decision that nobody could possibly find a more beautiful theme for GDM than the one included with the distro and therefore took out the ability to change it.

Luckily, some other nice people disagreed with this myopic form of thinking and released [some of their own themes for Ubuntu 9.10]("http://www.ubuntugeek.com/nice-themes-for-ubuntu-9-10-karmic-users.html")

Edit :: I was wrong, this does not change the GDM theme, only the user's theme. The only thing I found possible was changing the wallpaper in the login screen by doing > gksudo -u gdm dbus-launch gnome-appearance-properties

---

### Post by Donalb on 2009-11-05
Here: (if you can follow it, I couldn't)

[http://lionlix.wordpress.com/2009/10/23/hack-ubuntu-9-10-karmic-koala-gdm-login-screen/](http://lionlix.wordpress.com/2009/10/23/hack-ubuntu-9-10-karmic-koala-gdm-login-screen/)

---

### Post by mikerobinson on 2009-11-05
> **Donalb said:**
> Here: (if you can follow it, I couldn't)

[http://lionlix.wordpress.com/2009/10/23/hack-ubuntu-9-10-karmic-koala-gdm-login-screen/](http://lionlix.wordpress.com/2009/10/23/hack-ubuntu-9-10-karmic-koala-gdm-login-screen/)

Again, this only allows you to change very basic options like background image, mouse pointer, etc. It is far more complicated than the command I mentioned above and doesn't achieve anything else.

---

### Post by saivin on 2009-11-07
Mike, tried ur command. but it is just command line launching of 'Preferences -> Appearance'. :-( The other linked article didn't work at all. gave some error...

I guess its not the fault of Ubuntu developers. Its the Gnome developers who are over-smart. I have fedora too and I can't change gdm theme even there.

Now, I understand why Linus commented Gnome treats users as if they are stupid... Grrr...

---

### Post by Aflack on 2009-11-07
Well this is disappointing lol.

---

### Post by kartook on 2009-11-08
> **mikerobinson said:**
> The Ubuntu developers made the executive decision that nobody could possibly find a more beautiful theme for GDM than the one included with the distro and therefore took out the ability to change it.

Luckily, some other nice people disagreed with this myopic form of thinking and released 

What is it mean called OpenS0urce !!!!.I am looking for Customized and handy OS ..This is cool I moving back kubuntu 9.04 or ubuntu 9.04 

Thanks 
Mr.K~

---

### Post by haritia on 2009-11-08
> **scottpledger said:**
> How does one change the gdm theme in 9.10?

So it's now like Windows and OsX then? I sincerely hope this is a temporary situation like some on the boards are saying.

---

### Post by michaelzap on 2009-11-08
I haven't tried messing with the new GDM yet (although I will at some point, since I don't like to have to click on my name), but you can easily change the background image used by xsplash, including automatically whenever you change your desktop background:
[http://www.omgubuntu.co.uk/2009/11/desktop-wallpaper-as-xsplash.html](http://www.omgubuntu.co.uk/2009/11/desktop-wallpaper-as-xsplash.html)

I use this along with the Wallpaper Tray applet to rotate my desktop background and xsplash image constantly. This improved my bootup angst considerably, since I really hated that spotlight background. I had so many nice GDM themes collected in Jaunty that I really did miss them.

---

### Post by ibuclaw on 2009-11-08
> **mikerobinson said:**
> The Ubuntu developers made the executive decision that nobody could possibly find a more beautiful theme for GDM than the one included with the distro and therefore took out the ability to change it.


Wrong, this was the design made by the gnome developers. Ubuntu had no dictation in how easy/difficult it is to change the theme. The fact that it is a little more difficult that gdm2.24 is just.

Now, if I recall correctly, the new gdm is alot heavier than the old, hence the need to drop alot of features.

The simple way to do it would be:
```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```
then logout. The dm will open immediately the "Appearances" window, here, you can change the theme to what suits.

Once done, close the window and login, then remove the desktop file:
```
sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

As for xsplash, one way to do it would be to divert the current image:
```
sudo dpkg-divert --local --rename --add /usr/share/images/xsplash/bg_2560x1600.jpg
```
Then copying a background there in it's place.

ie:
```
sudo cp /usr/share/backgrounds/TheRainbowisDead.jpg /usr/share/images/xsplash/bg_2560x1600.jpg
```

Regards
Iain

---

### Post by snailhead on 2009-11-08
While all of tinivole's instructions are workable, I think he's missing the point:
1) The current greeter displays users
2) The ability to alter this configuration of the greeter appears to have been lost
3) and in my case, gdm no longer pays attention to which console it defaults its display

So, I suggest that this may work as it did for me (as root or sudo):
Stop the gdm service
apt-get remove gdm
apt-get install gdm-2.20

and I had to add a soft link so that /usr/X11R6/bin/X was once again valid
ln -s ../usr X11R6 in /usr

Alternatively, edit /etc/gdm/gdm.conf

Restart the gdm service

I did get one more error from gnome when I logged in.  So I suspect that gdm-2.20 may negatively affect fast user switching.  But in my household, *nobody* except myself is brave enough to run Un*x.

As for why gnome / ubuntu developers decided this path, I would disagree with tinivole's assertion in a minor fashion: I think this was a coordinated effort to irritate the current user base so as to be more attractive to those Windows 7 users who are use to living in user jail hell.  They got feedback that the new greeter while "pretty" wasn't acceptable, they choose to ignore that feedback.


> **tinivole said:**
> Wrong, this was the design made by the gnome developers. Ubuntu had no dictation in how easy/difficult it is to change the theme. The fact that it is a little more difficult that gdm2.24 is just.

Now, if I recall correctly, the new gdm is alot heavier than the old, hence the need to drop alot of features.

The simple way to do it would be:
```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```then logout. The dm will open immediately the "Appearances" window, here, you can change the theme to what suits.

Once done, close the window and login, then remove the desktop file:
```
sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```As for xsplash, one way to do it would be to divert the current image:
```
sudo dpkg-divert --local --rename --add /usr/share/images/xsplash/bg_2560x1600.jpg
```Then copying a background there in it's place.

ie:
```
sudo cp /usr/share/backgrounds/TheRainbowisDead.jpg /usr/share/images/xsplash/bg_2560x1600.jpg
```Regards
Iain

---

### Post by ibuclaw on 2009-11-09
> **snailhead said:**
> While all of tinivole's instructions are workable, I think he's missing the point:
1) The current greeter displays users

Fix:
```
sudo -u gdm gconftool-2 --set /apps/gdm/simple-greeter/disable_user_list --type bool true
```
> **snailhead said:**
> 
2) The ability to alter this configuration of the greeter appears to have been lost

See above fix to see why this statement is false.
More configuration options can be found [here.]("http://library.gnome.org/admin/gdm/2.26/configuration.html.en_GB")
> **snailhead said:**
> 
3) and in my case, gdm no longer pays attention to which console it defaults its display

It's always been tty7 ? (With the exception of Fedora, that have defaulted it to tty1 for KMS integration).
> **snailhead said:**
> 
As for why gnome / ubuntu developers decided this path, I would disagree with tinivole's assertion in a minor fashion: I think this was a coordinated effort to irritate the current user base so as to be more attractive to those Windows 7 users who are use to living in user jail hell.  They got feedback that the new greeter while "pretty" wasn't acceptable, they choose to ignore that feedback.
That is a very brave assumption, considering it is your first post, my friend.

Regards
Iain

---

### Post by jaybee99 on 2009-11-10
> **tinivole said:**
> Fix:
```
sudo -u gdm gconftool-2 --set /apps/gdm/simple-greeter/disable_user_list --type bool true
```



Thankyou! It depresses me that ubuntu and gnome are becoming more difficult to configure. All I wanted to do was turn off the login sound, stop displaying a list of users and log in to a default X session. Those used to be easy things to do. Still, all's well that ends well.

---

### Post by eric9477 on 2009-11-10
I think the point he's trying to make in a roundabout way, is that one of the many attractive things about Ubuntu/Gnome/open-source is that it offers a level of customization that Windows lacks. Changing the login theme seems to be a popular functionality and it's taking a step backwards to force users to search forums for workarounds to do something that was once an easy and intuitive process.  Hopefully it was an oversight and will be back in the next version.  In the meantime, thanks for the fixes. :D

> **tinivole said:**
> Fix:
```
sudo -u gdm gconftool-2 --set /apps/gdm/simple-greeter/disable_user_list --type bool true
```

See above fix to see why this statement is false.
More configuration options can be found [here.]("http://library.gnome.org/admin/gdm/2.26/configuration.html.en_GB")

It's always been tty7 ? (With the exception of Fedora, that have defaulted it to tty1 for KMS integration).

That is a very brave assumption, considering it is your first post, my friend.

Regards
Iain

---

### Post by BrHa on 2009-11-11
For my part I dropped GDM 2.28 on 9.10 to revert to the GDM 2.20 legacy you can find on Synaptic ... This will enable you to have the old GDM and have the flexibility of the GDM Theme change and usual login flexibility you could find in Sys > Admin > Login Window...

Cheers,
BrHa

---

### Post by jayanramesh on 2009-11-18
To whomever so  it may concern ,(ubuntu forum staff),
It is highly obnoxious,irritable and pathetic to abolish and [COLOR="Red"]_take out the freedom to change the GDM theme _[/COLOR]-deviating from the best to the worst?.[COLOR="SeaGreen"]The LINUX-[/COLOR] the open source -should allow nobody to restrict anybody's FREEDOM saying or rationalising on some points.I(we) as a common man do highly esteem you(all who create THE LINUX-ubuntu world).The decision should not derived from any group of people and rather from everyone.Again and I reiterating It is the open source -**[COLOR="Red"]THE LINUX[/COLOR]** not the windows.I as a individual and like everyone who immensely and intensely love and admire -LINUX deeply concern over the way it changed the GDM theme.
Thank you.

---

### Post by Redsandro on 2009-11-18
My God this is annoying. I don't know who made some kind of 'feature' that is greater than easy customization, but this makes everyone involved look bad.

If you don't like to choose from all those different commands posted above, I suggest reverting to GDM 2.20 via Synaptic like **BrHa** suggested.

You don't have to set any forced switch, gdm-2.20 is right there in the repo (named legacy) and it will automatically remove the 'new' gdm.

[B]-edit-

[COLOR="Red"]NO WAIT![/COLOR][/B]

On Xubuntu 9.10 it will break your machine :( Now I don't know how to get the cool login screens back. :(

---

### Post by jaybee99 on 2009-11-18
> **jayanramesh said:**
> To whomever so  it may concern ,(ubuntu forum staff),
It is highly obnoxious,irritable and pathetic to abolish and [COLOR="Red"]_take out the freedom to change the GDM theme _[/COLOR]-deviating from the best to the worst?.[COLOR="SeaGreen"]The LINUX-[/COLOR] the open source -should allow nobody to restrict anybody's FREEDOM saying or rationalising on some points.I(we) as a common man do highly esteem you(all who create THE LINUX-ubuntu world).The decision should not derived from any group of people and rather from everyone.Again and I reiterating It is the open source -**[COLOR="Red"]THE LINUX[/COLOR]** not the windows.I as a individual and like everyone who immensely and intensely love and admire -LINUX deeply concern over the way it changed the GDM theme.
Thank you.

It might sound like you're overreacting, but I also think it's a very bad sign. Canonical are primarily concerned with poaching windows users and have ended up with something that is not as flexible as a distro ought to be. Why should it be difficult to install slim and use that instead of gdm? There just isn't any excuse. I've switched to Arch and it's great. The most fun I've had since Warty.

Bye, and thanks a lot for the help!

---

### Post by Redsandro on 2009-11-18
I thought someone mentioned it is not Canonical but Gnome who imposes these changes? Not true?

I might switch to Debian, sort of Ubuntu before Canonical changed it for the good and the bad. But I am not sure if it is too difficult for me (installation).

---

### Post by jaybee99 on 2009-11-18
> **Redsandro said:**
> I thought someone mentioned it is not Canonical but Gnome who imposes these changes? Not true?

I might switch to Debian, sort of Ubuntu before Canonical changed it for the good and the bad. But I am not sure if it is too difficult for me (installation).

It sounds like the gdm defaults thing is down to GNOME, but I was speaking more generally. I don't know if the problems I had removing gdm were due to Canonical or GNOME, but I strongly object to the choice being taken out of my hands, so maybe I shouldn't be using a distro which is so tied in to GNOME. (That's a rhetorical maybe, I definitely shouldn't.) 

Debian installation isn't that hard, install virtualbox and give it a try in a safe enviroment.

---

### Post by Redsandro on 2009-11-18
Yeah I think I will try that. (virtual debian installation)

By the way, Xubuntu (not tied to Gnome very much) also uses gdm and it breaks when going back to 2.20. Now I don't dare to retry. Guess they won. Windows syndrome. ;)

---

### Post by eric9477 on 2009-11-18
> **jaybee99 said:**
> maybe I shouldn't be using a distro which is so tied in to GNOME. (That's a rhetorical maybe, I definitely shouldn't.) 

There's always Kubuntu I guess.  I may switch to KDE myself on the next upgrade.

---

### Post by coCoKNIght on 2009-11-18
> **tinivole said:**
> 
The simple way to do it would be:
```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```
Xubuntu lacks this file. Any idea as to how to do it with Xubuntu?

---

### Post by jaybee99 on 2009-11-18
> **eric9477 said:**
> There's always Kubuntu I guess.  I may switch to KDE myself on the next upgrade.

I switched to Arch and am very happy with it. Booting up and general operation is much faster and there is nothing installed that I didn't ask for. I can change any aspect of config by editing text files and on the command line. Not for everybody but suits me, and reminds me why I liked GNU/Linux in the first place.

I hope it doesn't sound like I'm trolling. I like ubuntu, and the best thing about it is the community.

---

### Post by eric9477 on 2009-11-18
> **jaybee99 said:**
> I switched to Arch and am very happy with it. Booting up and general operation is much faster and there is nothing installed that I didn't ask for. I can change any aspect of config by editing text files and on the command line. Not for everybody but suits me, and reminds me why I liked GNU/Linux in the first place.

I hope it doesn't sound like I'm trolling. I like ubuntu, and the best thing about it is the community.

Yeah, I tried several different distros before Ubuntu.  The community and ease of operation is what sold me.  I wanted to do as little command line and text file editing as possible :)

---

### Post by Kossilar on 2009-11-19
IMHO I don't see a valid reason for this functionality to be removed. Its an obvious feature and the idea that anybody in the FOSS community would remove an obvious feature from Ubuntu is totally alien to me. 

I feel like I just opened up a new version of Firefox and discovered that tabbed browsing is gone. 

If they were going to do this they should have at least given us a few options to choose from. I *hate* the current one. Gonna have to see if KDE is up to scratch yet I guess.

---

### Post by growlf on 2009-11-19
Well, not only do I not see any reason for removing the option to change the GDM theme, but I find this an unacceptable security flaw for systems that I have installed in a public/multiuser environment.  Basic security concepts are now violated by showing the usernames list without the option of hiding them and then forcing the user to type in the correct username.

The customization of the background image is nice and all (even if we have to do it via cmdline now) but does not address the far more important issues - at least not for me.

Bad.  Very bad.  This issue will cause me to have to switch distros very soon... on alot of computers.  Not pleased, to say the least.

---

### Post by coCoKNIght on 2009-11-19
growlf: I think you'll be able to resolve your issue by reading [http://library.gnome.org/admin/gdm/2.26/configuration.html.en_GB#greeterconfiguration](http://library.gnome.org/admin/gdm/2.26/configuration.html.en_GB#greeterconfiguration)
or by following the steps described in [http://ubuntuforums.org/showthread.php?p=8312301](http://ubuntuforums.org/showthread.php?p=8312301)
I prefer a login without user list too

---

### Post by michaelzap on 2009-11-19
@growlf: I agree with you. It is possible to change this behavior, however. All you need to do is enter this one command into a terminal:
```
sudo -u gdm gconftool-2 --set --type boolean /apps/gdm/simple-greeter/disable_user_list true
```

I found that info [here]("http://ubuntuforums.org/showpost.php?p=8307472&postcount=2"), and it worked for me.

---

### Post by growlf on 2009-11-19
Awesome @michaelzap - that actually did it. I had tried using the gconf GUI - to no avail.  I think, in retrospect, I may have neglected to sudo to 'gdm' first when I tried it that way.

Thank you both for the replies - that solved my biggest concern.  I still think Gnome needs to put that back into the normal GUI, however.

---

### Post by growlf on 2009-12-21
...aaaand after yesterdays updates were done and I rebooted - it's back again.  Drop down login.  Niiiice.  *sigh*

This is just ridicules.  I am thinking Kubuntu might just be an option at this point.  Used to like it a few years back...  may have to revisit it again.  Any better/other suggestions?

With all of the clients that are complaining about Vista and now Win7 as well (the upgrade is about as clean as any other Windows - which is all too frequently buggy due to drivers or anitique sotware issues) I wanted to be able to offer a suggestion to upgrade to Ubuntu.  But, between this issue and a few others that are beginning to anoy me - I am holding back a bit this time.

---

### Post by exosyst on 2010-01-04
I made a tool to change a couple of the settings in an easier way [http://ubuntuforums.org/showthread.php?t=1358026](http://ubuntuforums.org/showthread.php?t=1358026)

Hope it helps alleviate some of these problems.

---

### Post by growlf on 2010-01-19
For those interested in a solution - Exosyst and I are now working together to make this a fully featured app and also to get a PPA published for it. 

You can find the most recent version of the GDM2Setup configuration tool on Launchpad [here]("https://launchpad.net/gdm2setup").  It works, it does the job, and we are going to add the rest of the functionality back into it as fast as we can.  For now, the important parts are already there, and we anticipate a beta installer for it within the next 2 weeks or so.

---

### Post by E-mol on 2010-01-20
Thank you so much - soon I will dare to look at my gdm again :)

---

### Post by growlf on 2010-01-20
FYI, there is an installer available now on [Launchpad]("http://launchpad.net/gdm2setup/0.2/0.3/+download/python-gdm2setup_0.3.0-1_all.deb").  

..also, check this thread for the instructions to add it in to your system with the updater: [GDM Configuration Tool]("http://ubuntuforums.org/showpost.php?p=8707543&postcount=55")

---

### Post by Copernicus1234 on 2010-01-24
I really hate when they remove things like this.

I was going to put in a new GDM theme but I guess I wont now. Thanks Gnome devs.

And yes, I can jump through the hoops mentioned in this thread when I have some more time, but the majority of people wont. They will just think it sucks that they cant change the GDM theme in Gnome from the menus.

---

### Post by Thomas Garman on 2010-01-24
Yes the commands given above do in fact cause the appearance box to pop up just like if you went to System --->  Preferences  ----> Appearance...

but how on earth can a person change that hideous login box that has my user name and asks for  a password?

I changed the splash screen and then did all of the other little tweaks suggested around the forums and now my dialogue box for login looks stupid, like windows 95 or something.  I have searched in vain for days looking for a way to change THAT.

I think it has something to do with the fact that the HUMAN theme was uninstalled when I installed some other theme... and sheesh, really, wby bother?  I am just leaving it the way it is.

---

### Post by tehweezil on 2010-03-19
> **mikerobinson said:**
> The Ubuntu developers made the executive decision that nobody could possibly find a more beautiful theme for GDM than the one included with the distro and therefore took out the ability to change it.

Luckily, some other nice people disagreed with this myopic form of thinking and released [some of their own themes for Ubuntu 9.10]("http://www.ubuntugeek.com/nice-themes-for-ubuntu-9-10-karmic-users.html")

Edit :: I was wrong, this does not change the GDM theme, only the user's theme. The only thing I found possible was changing the wallpaper in the login screen by doing

Yeah after I did that I have this annoying "Assistive Technologies" daemon in my notification area and if I kill it,it changes my themes my window manager and everything. So how do I get rid of it? Because it's getting on my nerves

---

### Post by Penguin Guy on 2010-03-19
> **mikerobinson said:**
> The Ubuntu developers made the executive decision that nobody could possibly find a more beautiful theme for GDM than the one included with the distro and therefore took out the ability to change it.
They didn't just take out this feature for fun. They took it out to speed up boot time.

---

### Post by mikerobinson on 2010-03-20
> **tehweezil said:**
> Yeah after I did that I have this annoying "Assistive Technologies" daemon in my notification area and if I kill it,it changes my themes my window manager and everything. So how do I get rid of it? Because it's getting on my nerves

[http://ubuntuforums.org/showthread.php?p=8777169](http://ubuntuforums.org/showthread.php?p=8777169)

---

### Post by aravindprasad on 2010-04-14
I think they really wanted to make it **idiot proof for those Windows users** who are not used to customizing and if presented with the option would screw up their installation and then go around screaming like wuss-babies about how Linux is not friendly.

While that is probably not so bad, they could have had a **button saying "Advanced" for the Linux users** who are quite capable of handling themselves and live for the ability to customize everything.

-AP

---

### Post by tehweezil on 2010-04-14
> **aravindprasad said:**
> I think they really wanted to make it **idiot proof for those Windows users** who are not used to customizing and if presented with the option would screw up their installation and then go around screaming like wuss-babies about how Linux is not friendly.

While that is probably not so bad, they could have had a **button saying "Advanced" for the Linux users** who are quite capable of handling themselves and live for the ability to customize everything.

-AP

Pahahaha! Amen to that! :lolflag:

---

### Post by jaco223 on 2010-04-14
They really made changing the GDM theme next to impossible, or just plain impossible.
I've tried to follow the instructs throughout this thread, but for a n00b like me it is just
too much work. I hope at some point they make it*** easy*** to change the GDM theme.
Just my opinion.

Jaco

---

### Post by Snowhog on 2010-04-26
It is sad indeed. Individual customization of a Linux distro is, and always has been, a valued part of Linux et al. I just upgraded my Ubuntu Jaunty 9.04 this evening to Ubuntu Karmic 9.10. Imagine my frustration upon looking for and not finding the means to change the GDM Greeter to what I had been using before the upgrade. I thought that it was just buried in some sub-menu, and I just couldn't find it. Now I now why. Sad indeed.:(

Kubuntu (yes, I use it too) is still very customizable, even with the move to Plasma. Basics, like customizing the KDE Greeter, KSplash, and Grub 2 boot splash are still in the hands of the user, as it should be.

---

### Post by Redsandro on 2010-04-26
> **Snowhog said:**
> I just upgraded my Ubuntu Jaunty 9.04 this evening to Ubuntu Karmic 9.10.

Why would you do that? In 3 days 10.04 LTS is out! :)

---

### Post by towheedm on 2010-04-29
While GDM cannot be themed in the true sense of the word, it is highly customizable.  Check out the link at the beginning of this thread:
[http://ubuntuforums.org/showthread.php?p=9068333#post9068333](http://ubuntuforums.org/showthread.php?p=9068333#post9068333)

---

### Post by growlf on 2010-05-02
Wow Towheedm!  Very nice.  Well done.  Thank you!

---

### Post by towheedm on 2010-05-04
> **growlf said:**
> Wow Towheedm!  Very nice.  Well done.  Thank you!

You are most welcome, glad to give back to a community that's helped me so much.

---

### Post by CNBarnes on 2010-05-06
I'm going to add to this thread, even though I think I already know what you folks are going to say.

I run a small student computer lab (16 computers).  The computers authenticate off of an LDAP server, which means I certainly don't want (can't have) logon icons shown.

I just installed 10.04.  


Is there ANY way for the logon screen to have 2 blank fields, one for userid & one for password?  I can't believe that there isn't some way to customize this...

---

### Post by growlf on 2010-05-06
> **CNBarnes said:**
> Is there ANY way for the logon screen to have 2 blank fields, one for userid & one for password?  I can't believe that there isn't some way to customize this...

Certainly.  You can use the GDM2Setup tool (found at [https://launchpad.net/gdm2setup](https://launchpad.net/gdm2setup)) or do it manually via the commandline:

```
sudo -u gdm gconftool-2 --set --type boolean /apps/gdm/simple-greeter/disable_user_list true
```

If you are using an LDAP server, you are probably doing something for remote management and package maintenance, so the commandline method may be your best bet unless you want to perform the task on each computer.  On the other hand - you have easy access to several other features with GDM2Setup as well. There are commanline solutions to everything in GDM2Setup (and more), which can be found in Towheedm's excellent doc a couple posts up from here also.

---

### Post by towheedm on 2010-05-06
> **growlf said:**
> There are commanline solutions to everything in GDM2Setup (and more), which can be found in Towheedm's excellent doc a couple posts up from here also.

Yo can download the document from the link at the beginning of this thread:
[http://ubuntuforums.org/showthread.php?p=9068333#post9068333](http://ubuntuforums.org/showthread.php?p=9068333#post9068333)

---

### Post by towheedm on 2010-05-06
> **growlf said:**
> There are commanline solutions to everything in GDM2Setup (and more), which can be found in Towheedm's excellent doc a couple posts up from here also.

Yo can download the document from the link at the beginning of this thread:
[http://ubuntuforums.org/showthread.php?p=9068333#post9068333](http://ubuntuforums.org/showthread.php?p=9068333#post9068333)

---

### Post by towheedm on 2010-05-06
> **growlf said:**
> There are commanline solutions to everything in GDM2Setup (and more), which can be found in Towheedm's excellent doc a couple posts up from here also.

The document can be downloaded from the link at the beginning of this thread:
[http://ubuntuforums.org/showthread.php?p=9068333#post9068333](http://ubuntuforums.org/showthread.php?p=9068333#post9068333)

---

### Post by towheedm on 2010-05-06
The document can be downloaded from the link at the beginning of this thread:
[http://ubuntuforums.org/showthread.php?p=9068333#post9068333](http://ubuntuforums.org/showthread.php?p=9068333#post9068333)

---

### Post by towheedm on 2010-05-06
The document can be downloaded from the link at the beginning of this thread:
[http://ubuntuforums.org/showthread.php?p=9068333#post9068333](http://ubuntuforums.org/showthread.php?p=9068333#post9068333)

---

### Post by towheedm on 2010-05-06
You can download the document from the link at the beginning of this thread:
[http://ubuntuforums.org/showthread.php?p=9068333#post9068333](http://ubuntuforums.org/showthread.php?p=9068333#post9068333)

---

### Post by towheedm on 2010-05-06
You can download the document from the link at the beginning of this thread:
[http://ubuntuforums.org/showthread.php?p=9068333#post9068333](http://ubuntuforums.org/showthread.php?p=9068333#post9068333)

---

### Post by towheedm on 2010-05-06
Sorry for the redundant posts, have no idea what happened.  Because my reply was not showing,  posted several times.  Anyone knows how to delete the redundant posts?

---

### Post by CNBarnes on 2010-05-07
> **growlf said:**
> If you are using an LDAP server, you are probably doing something for remote management and package maintenance...


Funny you should mention this.  :KS

This computers are dual boot Win7/Ubuntu 10.04.  In the past, we've used Symantec Ghost to image a 'master' computer then copy the image to all of the lab computers simultaneously.   However, it seems that Symantec Ghost doesn't understand ext4 (and Ubuntu 10 only wants to use ext4).  Which means I have a whole 'other issue to deal with - but I'll start a different thread for that rather than hijack this one (further). :lolflag:

---

### Post by tehweezil on 2010-05-09
Meh. I just upgraded to Lucid aannnndddd the default Login Screen application is still retarded. awesome. :/

---

