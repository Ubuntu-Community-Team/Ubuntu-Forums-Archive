---
title: "UIM lists no languages in the input method switcher"
date: 2008-10-19
forum: General Help
---

### Post by CharonM72 on 2008-10-19
As is stated in the title. However, all the IMs (of which there are a *lot*, in my case), appear in every menu in UIM preferences. I have UIM 1.5.3 and Ubuntu 8.04. This occurs with uim-toolbar-gtk, uim-toolbar-gtk-systray, and uim-toolbar-qt. uim-module-manager lists all the modules as registered.

Oh, and this could have to do with it- my IM env variables at login are all scim, even though I manually changed them in /etc/X11/xinit/xinput.d to uim, in accordance to the link in ~/.xinput.d. Maybe something is exporting the new variables after xinit runs...? SCIM is uninstalled by the way.
Although after changing the env's back to uim in my current session, UIM still doesn't work.

Thanks in advance! although judging from my last help threads, nobody's gonna post...

---

### Post by tacutu on 2008-10-19
it's been a long time since I used uim... could you post the output of
```
export | grep IM
```
?

Also, any reasons for not using scim?

---

### Post by CharonM72 on 2008-10-19
```
declare -x GTK_IM_MODULE="scim"
declare -x QT_IM_MODULE="scim"
declare -x XIM_PROGRAM="scim -d"
declare -x XMODIFIERS="@im=SCIM"
```

Oh my, that seems problematic...

And SCIM was working fine 'till it got even more problems than UIM has (namely, crashing almost every program every 10 seconds for no reason). So I ended its miserable life. Also, UIM looks great (when it works) so I'd prefer to not have to default back to SCIM.

---

### Post by tacutu on 2008-10-19
hmm, this is strange. I just installed uim fom the repos and it works for me.

after installation, I did```
im-switch -c
``` and selected "uim-systray"
(dunno the difference bet. systray and tooldbar, but I assume both would work)
Then <CTRL><ALT><BACKSPACE> to restart the X server and after logging in, I get:
```
 export | grep uim
declare -x GTK_IM_MODULE="uim"
declare -x QT_IM_MODULE="uim"
declare -x XMODIFIERS="@im=uim"
```
 and uim works just fine.

What are the exact steps you followed?

---

### Post by CharonM72 on 2008-10-19
I couldn't possibly list all my steps. I did what you did and selected toolbar, and the toolbar appears at login, yet it still refuses to change to any IM aside from this one. Also, the export | grep im still lists:

```
declare -x GTK_IM_MODULE="scim"
declare -x QT_IM_MODULE="scim"
declare -x XIM_PROGRAM="scim -d"
declare -x XMODIFIERS="@im=SCIM"
```

And here's my /etc/X11/xinit/xinput.d/uim-toolbar file:

```
# uim with GTK toolbar indicator
XIM=uim
XIM_PROGRAM=/usr/bin/uim-toolbar-gtk
XIM_ARGS=
GTK_IM_MODULE=uim
QT_IM_MODULE=uim
# It seems to me that the system needs to be initialized.
# Folowing trick will wait 10 seconds without slowing down X start up.
XIM_PROGRAM_XTRA="(sleep 10; uim-toolbar-gtk)"
DEPENDS="uim-xim,uim-gtk2.0|uim-qt,uim-anthy|uim-canna|uim-prime|uim-skk|uim-m17nlib"
```

Although even if I got that fixed I'd still need to get UIM to let me change input methods. Right-click and click on "Switch input method"- a box should pop up, presumably with input methods in it (although maybe not in your case if you didn't install any IMEngines). Anyway, I have every IMEngine I could find, and my box is completely blank.

I installed UIM from source though, and not from the repository. When I did it from the repos it did the exact same thing, so I thought I'd try source.

By the way, thanks for finally replying. You're the only person in the 5 or so threads I've made (in other sites).

---

### Post by tacutu on 2008-10-19
clearly the problem is due to the wrong variables, i.e. the IM_MODULE which should be uim, not scim...
what's the output of 
```
ls -l ~/.xinput.d/
```?

mine shows all_ALL as a symlink pointing to 
/etc/X11/xinit/xinput.d/scim-bridge (what I use, yours should be uim-{systray/toolbar} and also  en_US pointing to the same file.

Well, I do like to help, but it seems I don't really have the expertise.

---

### Post by CharonM72 on 2008-10-19
I got:

```
total 0
lrwxrwxrwx 1 <username> <username> 35 2008-08-07 19:05 en_GB -> /etc/X11/xinit/xinput.d/scim-bridge
lrwxrwxrwx 1 <username> <username> 27 2008-10-19 04:05 fr_FR -> /etc/X11/xinit/xinput.d/uim
lrwxrwxrwx 1 <username> <username> 35 2008-10-19 04:05 fr_FR.backup -> /etc/X11/xinit/xinput.d/uim-toolbar
```

Heh well all I use is en_GB or fr_FR, so that's all that's here...
I should change en_GB to uim at some point. But right now I'm booting fr_FR locale, which should load uim (and it does). Of course, the env's are wrong nonetheless, which is puzzling :confused:
My /etc/X11/xinit/xinput.d/uim is exactly the same as ./uim-toolbar except it doesn't load the toolbar.

I need to go to bed before sunrise, but I'll be right back on this later today. I'll fix en_GB when I come back but I highly doubt it'll have an effect. Thanks for your help so far- anything helps, especially when UIM doesn't have any real form of tech support that I can find.

---

### Post by tacutu on 2008-10-19
This might be the culprit.
Are you 100% sure your current locale is fr_FR?
Type
```
locale
```
to make sure.

Also, I don't know if it matters, but is your default encoding utf8? I seem to remember some days when, if you wanted Japanese input, you had to set the locale to ja_JP and a japanese encoding, but I don't think that's the case anylonger.

---

### Post by CharonM72 on 2008-10-19
```
LANG=fr_FR.UTF-8
LC_CTYPE="fr_FR.UTF-8"
LC_NUMERIC="fr_FR.UTF-8"
LC_TIME="fr_FR.UTF-8"
LC_COLLATE="fr_FR.UTF-8"
LC_MONETARY="fr_FR.UTF-8"
LC_MESSAGES="fr_FR.UTF-8"
LC_PAPER="fr_FR.UTF-8"
LC_NAME="fr_FR.UTF-8"
LC_ADDRESS="fr_FR.UTF-8"
LC_TELEPHONE="fr_FR.UTF-8"
LC_MEASUREMENT="fr_FR.UTF-8"
LC_IDENTIFICATION="fr_FR.UTF-8"
LC_ALL=
```

If fr_FR.UTF-8 different than fr_FR? And yes, having UTF8 allows me to use any IM for anything.

---

### Post by tacutu on 2008-10-20
> **CharonM72 said:**
> 
If fr_FR.UTF-8 different than fr_FR? 

I guess it just selects the encoding... having UTF8 can't be wrong, anyway.

I'm eager to know what happens once you change the en_GB in .xinput.d to point to uim... but I'm afraid it won't solve your problem.

what about creating an .xinitrc file in your home containing:

```

XIM=uim
XIM_PROGRAM=/usr/bin/uim-xim
XIM_ARGS=
GTK_IM_MODULE=uim
QT_IM_MODULE=uim
exec gnome-session

```
(assuming you're using gnome)
It might be worth a try.

---

### Post by CharonM72 on 2008-10-20
Good news 1: it didn't crash my system like it did last time i tried editing xinit
Good news 2: it successfully changed all my env's, so now uim functions as my input method, and the bar even changes to reflect that
Bad news 1: uim-pref-gtk now crashes with a "segmentation fault" error
Bad news 2: the list of input methods is still empty, leaving me only able to use direct input

So I'm making progress, but not out of the woods yet...

EDIT: I ran uim-pref-qt with success, and changed my default input method there to Anthy with the ability to switch to Direct by hotkey. Typing in gedit was still direct, and by pressing the hotkey, a box (which was supposed to show the input method, but was empty) appeared, and it continued to be direct.

EDIT AGAIN: Now it's more fixed- I reinstalled uim completely, this time through the repos, and now Anthy works as the default IM, and it allows me to switch among T-code, Try-code, TUT-code, and VIQR in gedit, but for some reason won't change out of direct here in Firefox. Also, now both uim-pref-gtk and uim-pref-qt all crash, as well as uim-im-switcher-qt with a segmentation fault. uim-im-switcher-gtk still works, but lists no IMs.

EDIT AGAIN AGAIN: I uninstalled every IM except Anthy, and the same problem persists after restarting uim. Note I'm using uim-applet-gnome in my taskbar as my uim applet. The toolbar fails to as much as change at all when I select somewhere to input text.

---

### Post by tacutu on 2008-10-21
I' afraid this is as far as I can help you... I have no idea what would be the next step. However, uim segfaulting sounds rather bizarre. I wonder if something is wrong with your ubuntu installation.

Just out of curiosity,what happens if you create a new user? Does uim work for the new user ordoes it have the same odd behavior?

---

### Post by CharonM72 on 2008-10-21
Same behavior. I filed a bug report to see if maybe the creators might have an idea of what may be happening.
Good news though- after reinstalling scim it suddenly works now. So I can use that until I can get uim fixed.

---

### Post by Razlo on 2010-02-14
> **tacutu said:**
> hmm, this is strange. I just installed uim fom the repos and it works for me.

after installation, I did```
im-switch -c
``` and selected "uim-systray"
(dunno the difference bet. systray and tooldbar, but I assume both would work)
[...]

Hey! Thanks a lot! Japanese input works perfectly now. I got here googling first how to install scim, then ibus, and finally for uim. In ubuntu 8.04 I was able to make scim work at 100%, but I spent lots of time more.

Thx once more ;)

---

