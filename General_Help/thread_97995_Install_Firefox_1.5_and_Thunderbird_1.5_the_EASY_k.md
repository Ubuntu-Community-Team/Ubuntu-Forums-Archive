---
title: "Install Firefox 1.5 and Thunderbird 1.5 the EASY klik way"
date: 2005-12-02
forum: General Help
---

### Post by KillerKiwi on 2005-12-02
Install Klik
Press Alt-f2 and paste
```
wget klik.atekon.de/client/install -O -|sh
```

Then click these links
[klik://firefox]("klik://firefox")
[klik://thunderbird]("klik://thunderbird")

To delete(uninstall) just trash the file on your desktop

---

### Post by manicka on 2005-12-02
Interesting, does the klik version pick up all the plugins and flash, java etc correctly? Can they be set as the default versions?

---

### Post by DimaIL on 2005-12-02
Nice idea!
Which more applications there are in Klik?

EDIT: If I want to install skype through klik, may i install all supports(qt,lib...) alone or it will install them together?

Thanks!
Dima.

---

### Post by BathroomNinja on 2005-12-02
Interesting.  I somehow bombed the install with the tar last night, so I will give this a try when I get home.

---

### Post by DimaIL on 2005-12-03
does it works? i tryed it and it writes "klik is not a registered protocol"
What is the problem?

Thanks
Dima

---

### Post by metrorobo on 2005-12-03
I installed FF 1.5 through klik and it works really well. My themes and Extensions got recognized, minus the ones that don't work with 1.5.
However, 2 things bug me.
One is about a message being displayed when opening FF once in awhile concerning something about chrome.
The other is that my plugins weren't recognized and I don't know how to get them working in this.
Installing FF this way does beat installing it the manual way, or having to wait for it to be backported.

I also wanted to point out, FF 1.5 seems to work really well in Ubuntu. Pretty fast and smooth I must say.

---

### Post by python_boot on 2005-12-03
I want to preface this post by stating that I am a total Ubuntu newbie.

I have installed Klik and used it to insall FireFox and Thunderbird 1.5, but (and this is completely embarrassing) *I cannot figure out how to launch FF 1.5 from the GUI*. The Applications menu points to FF and TB 1.07, and I don't know enough about where apps are installed in Linux to find the FF1.5 executable and add it to the app menu. **I was really hoping that installing 1.5 would replace 1.07, but apparently that was silly of me.**:( 

If anyone has any suggestions for me, I would appreciate it. Until then, I'll just try to monkey with this and see if I can't make it do what I want.

{EDIT}
Waitaminute...

The .CMG file on my Desktop is the link to execute FF 1.5? That seems kind of...strange. Could someone clarify why it works that way?

---

### Post by manicka on 2005-12-03
[QUOTE=python_boot]

{EDIT}
Waitaminute...

The .CMG file on my Desktop is the link to execute FF 1.5? That seems kind of...strange. Could someone clarify why it works that way?[/QUOTE]

That is correct. Klik packages are self contained and have everything they need within the CMG file. A bit like the way applications work on MacOS X.

---

### Post by manicka on 2005-12-03
[QUOTE=metrorobo]
The other is that my plugins weren't recognized and I don't know how to get them working in this.
Installing FF this way does beat installing it the manual way, or having to wait for it to be backported.
[/QUOTE]


hmm, I disagree. If using the klik package doesn't pick up your plugins and they don't work, then it''s a waste of time. 
You'd be better off spending a bit more time on a method that works ( [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) ) with all plugins and  themes useable from the get go.

---

### Post by KillerKiwi on 2005-12-04
> does it works? i tryed it and it writes "klik is not a registered protocol"

You need to restart firefox after installing the klik client

klik does still have a few rough edges(re java + flash in ff), but i think its a big step forward in installing third party apps on a linux distro

> EDIT: If I want to install skype through klik, may i install all supports(qt,lib...) alone or it will install them together?


Not sure I already had the qt base installed and it just worked for me, im pretty sure klik packages do NOT include kde base though

---

### Post by discord on 2005-12-04
It's not really hard to install using the directions posted on the wikipage. Thats what I'd reccomend. You can automate the process by using semicolons and gedit. for example to enter two commands in the terminal at once you could paste


cd /usr/lib;
mkdir java;

someone could make a bash script for the wikipage also...

---

### Post by discord on 2005-12-04
I'm pretty happy with apt and synaptic personally. Only when i need the latest version of an app do i go get its installer... The debs are catered to us and our distro..


>klik does still have a few rough edges(re java + flash in ff), but i think its a big >step forward in installing third party apps on a linux distro

---

### Post by manicka on 2005-12-04
[QUOTE=discord]

someone could make a bash script for the wikipage also...[/QUOTE]

I believe arnieboy is working on something similar as part of [Automatix]("http://ubuntuforums.org/showthread.php?t=66563"). Apparently it's not as easy as it would appear.

---

### Post by magnusbb on 2005-12-04
I tried out Klik, and while it's an interessting idea, I prefer the native way for my distribution. In the future, though, this can be great, but the cooperation between the Klik team and the distributions has to be better, to make it work seamless.

But try to unistall Klik. That's not easy done, it actually involves more than fifteen clicks and some brain activity. There is a unisntall script, but it does not work properly - it doesn't remove all the files. I would like to have a clean system, and this kind of cluttering without a decent uninstall method is not good. I am talking about the Klik client itself now, not the different programs available through Klik - that's easy as pie.

---

### Post by cutOff on 2005-12-04
[QUOTE=manicka]hmm, I disagree. If using the klik package doesn't pick up your plugins and they don't work, then it''s a waste of time. 
You'd be better off spending a bit more time on a method that works ( [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) ) with all plugins and  themes useable from the get go.[/QUOTE]
manicka, does your FF recognize java & flash plugins? It seemed to me so.

---

### Post by aldmal on 2005-12-04
Thank you, thank you, thank you!!!!!! :smile: 

I'm a newbie and have messed around trying to get Firefox 1.5 to the correct directries on my puter. No luck

A few minutes at klik and I'm all done. Grabbed some other apps at the same time. This site will help to kill Windows. Great!!!

Thanks again

---

### Post by cutOff on 2005-12-04
[QUOTE=aldmal]Thank you, thank you, thank you!!!!!! :smile: 

I'm a newbie and have messed around trying to get Firefox 1.5 to the correct directries on my puter. No luck

A few minutes at klik and I'm all done. Grabbed some other apps at the same time. This site will help to kill Windows. Great!!!

Thanks again[/QUOTE]
heh, you're welcome ;)

---

### Post by KillerKiwi on 2005-12-04
[QUOTE=aldmal]Thank you, thank you, thank you!!!!!! :smile: 

I'm a newbie and have messed around trying to get Firefox 1.5 to the correct directries on my puter. No luck

A few minutes at klik and I'm all done. Grabbed some other apps at the same time. This site will help to kill Windows. Great!!!

Thanks again[/QUOTE]

And that about sums up the whole reason for klik :) 

P.S. to all command line users you are NOT the target audience

---

### Post by Mguel on 2006-03-03
I was wondering where does klik apps store the settings? are the setting files self contained also, or do they use the "usual" way?

I would love to be able to run self-contained apps in linux (besides from the regularly/repository installed files), on windows I used to use PortableFirefox, PortableOpenOffice, etc (which are apps in which all the app files and settings are contained under a folder):
[http://portableapps.com/](http://portableapps.com/)

I'm not sure if klik can acomplish this... (having also the settings self contained)

Cheers,
Mguel

---

### Post by nmastae on 2006-03-03
[QUOTE=KillerKiwi]Install Klik
Press Alt-f2 and paste
```
wget klik.atekon.de/client/install -O -|sh
```

Then click these links
[klik://firefox]("klik://firefox")
[klik://thunderbird]("klik://thunderbird")

To delete(uninstall) just trash the file on your desktop[/QUOTE]
I did this and I got the Run Application in ________ window. 
Which program do I choose?

Newbie.

---

### Post by towsonu2003 on 2006-03-03
[QUOTE=manicka]That is correct. Klik packages are self contained and have everything they need within the CMG file. A bit like the way applications work on MacOS X.[/QUOTE]
OMG! This is the portable application (portable firefox) thing for linux! cool!!

---

### Post by Mguel on 2006-03-03
Another question regarding klik: I get an error message: > Please install ar in order to use klik. I searched the forum and some others have the same problem, but haven't found the solution, nor the "ar" package on repositories to instal it.

Thanks in advance,
Mguel



[quote=Mguel]I was wondering where does klik apps store the settings? are the setting files self contained also, or do they use the "usual" way?

I would love to be able to run self-contained apps in linux (besides from the regularly/repository installed files), on windows I used to use PortableFirefox, PortableOpenOffice, etc (which are apps in which all the app files and settings are contained under a folder):
[http://portableapps.com/]("http://portableapps.com/")

I'm not sure if klik can acomplish this... (having also the settings self contained)

Cheers,
Mguel[/quote]

---

### Post by towsonu2003 on 2006-03-03
sudo apt-get install binutils

---

### Post by Mguel on 2006-03-03
[quote=towsonu2003]sudo apt-get install binutils[/quote]

Thanks! I just got the answer at:
[http://klik.atekon.de/wiki/index.php/Troubleshooting#I_get_.22Please_install_ar_in_order_to_use_klik.22](http://klik.atekon.de/wiki/index.php/Troubleshooting#I_get_.22Please_install_ar_in_order_to_use_klik.22)

Mguel

---

### Post by Mguel on 2006-03-03
[quote=Mguel]I was wondering where does klik apps store the settings? are the setting files self contained also, or do they use the "usual" way?

I would love to be able to run self-contained apps in linux (besides from the regularly/repository installed files), on windows I used to use PortableFirefox, PortableOpenOffice, etc (which are apps in which all the app files and settings are contained under a folder):
[http://portableapps.com/]("http://portableapps.com/")

I'm not sure if klik can acomplish this... (having also the settings self contained)[/quote]

It stores settings in the same place as "normal" firefox, (it uses your profile when running the firefox.cmg), so they are not self contained, and it can't accomplish something similar to PortableFirefox in windows :(

---

### Post by adamkane on 2006-03-06
How to add Firefox icon to Panel.

Right click the Panel -> Add to Panel... -> Custom Application Launcher

Name: Firefox
Command: /home/<username>/.zAppRun /<path to>/firefox.cmg
Icon: /<path to>/firefox.png

I tried ~/.zAppRun /<path to>/firefox.cmg, but it didn't function.

---

### Post by towsonu2003 on 2006-03-06
ah, doen't works for me... [http://www.knoppix.net/forum/viewtopic.php?t=23329&sid=de0e5f643da69d53db8abf05d35986b8](http://www.knoppix.net/forum/viewtopic.php?t=23329&sid=de0e5f643da69d53db8abf05d35986b8)

<soundeffect> pof </soundeffect>

---

### Post by Ptero-4 on 2007-02-09
klik apps doesn`t work in ppc computers. How do I fix it?

---

