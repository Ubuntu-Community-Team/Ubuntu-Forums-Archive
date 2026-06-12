---
title: "fprint - Fingerprint reader PAM login support with libfprint"
date: 2007-11-25
forum: Hardware &amp; Laptops
---

### Post by vishalrao on 2007-11-25
There are a few older fingerprint threads but I didn't see this mentioned so posting here.

I'm wondering if there is any chance of some sort of fingerprint based login support being added to Hardy Heron?

There is a new "fprint" project launched at [http://reactivated.net/fprint](http://reactivated.net/fprint) by Gentoo's Daniel Drake.

It has a few fingerprint readers supported for PAM logins including my AuthenTec AES1610 model on my HP Pavilion tx1302au tablet PC :-) See [http://reactivated.net/fprint/wiki/Supported_devices](http://reactivated.net/fprint/wiki/Supported_devices)

The ubuntu wiki page does not seem to be aware of this new project [https://wiki.ubuntu.com/FingerprintAuthentication](https://wiki.ubuntu.com/FingerprintAuthentication)

I couldn't find the developer section to post this, so posting here...

I tried the recently added aes1610 driver but fingerprint scan success/quality was not good, will try with the latest release and report it to them...
Other people report good success with libfprint and pam_fprint and the fprint_demo, but this is a young project and some minor issues exist.

---

### Post by drf_av on 2007-11-27
Impressed. I'm using sudo and gdm login with my fingerprint reader now. The only thing that's not working at the moment is gksu, but I'm really, really impressed.

---

### Post by mo0n_sniper on 2007-12-12
> **drf_av said:**
> Impressed. I'm using sudo and gdm login with my fingerprint reader now. The only thing that's not working at the moment is gksu, but I'm really, really impressed.

that's really really good!

can you share what you did with us ?

 :guitar: :guitar: Finally someone made it:guitar::guitar:

---

### Post by mo0n_sniper on 2007-12-13
Got it working too!!:guitar:

Now only my ati card needs decent hardware support.....

---

### Post by adam on 2007-12-15
Works for me!

Problems: 
1. pam-keyring won't work with pam-fprint, so I have to type the keyring password when I login. Just a minor annoyance.

2. gksu works but it won't tell you which finger you're supposed to scan and it doesn't fall back to a password like login/sudo does. 

I only have one finger enrolled which eliminates one of the gksu problems...  But is there some way to set different rules for gksu? Like, use fingerprint for login/sudo but have gksu just use a password?

---

### Post by Eddie Hung on 2007-12-22
> **adam said:**
> Works for me!

Problems: 
1. pam-keyring won't work with pam-fprint, so I have to type the keyring password when I login. Just a minor annoyance.

2. gksu works but it won't tell you which finger you're supposed to scan and it doesn't fall back to a password like login/sudo does. 

I only have one finger enrolled which eliminates one of the gksu problems...  But is there some way to set different rules for gksu? Like, use fingerprint for login/sudo but have gksu just use a password?

No I don't think there is: gksu/gksudo is simply a wrapper around the console based sudo, and they are both controlled by /etc/pam.d/sudo

There are fundamental flaws in the whole implementation, and I have described them extensively here:

[https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/15093](https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/15093)

(though it talks about pam_thinkfinger, it applies equally to pam_fprint - however I am very impressed that pam_fprint integrates so well with GDM and gnome-screensaver - the only remaining thing is if it can do the same to gksu - and it's something I'll look into if I have the time)

Eddie

---

### Post by drf_av on 2007-12-28
Ok I had some questions so I'll tell you how I made it. Note that my reader is an Authentec 2501, built into an HP laptop. It should work with every supported reader. Also note that THIS MIGHT BREAK YOUR SYSTEM SERIOUSLY!! So don't do it unless you know what you're doing.

For Italian folks, go ahead and [read my article here]("http://www.oneopensource.it/29/11/2007/fprint-il-tanto-atteso-supporto-ai-lettori-di-impronte-digitali/")

First of all you'll need to download and compile latest version of libfprint, pam_fprint, and fprint_demo.
You can find them [here]("http://reactivated.net/fprint/wiki/Main_Page"). Note that fprint may complain if libfprint is installed in /usr/local instead of /usr. This was for version 0.0.4, don't know if latest has still this behaviour. Anyway, if you get a "missing library error", try to install libfprint in /usr or create a symlink.

Once you're done, fire up fprint_demo and use it to enroll a finger. This will become the finger pam_fprint will ask for. If you're done, now edit /etc/pam.d/common-auth. It should be looking something like:

```
auth sufficient pam_fprint.so
auth sufficient pam_unix.so nullok_secure
```

Now restart and hopefully GDM and sudo will ask for your fingerprint, falling back in password mode if the fingerprint is wrong and/or cannot be obtained. This works with gnome-screensaver too.

The bad is that gksu window doesn't show up. Anyway, if you swipe your finger, the application will start correctly. Some hints and suggestions are welcome, also share with us if this method works for you.

---

### Post by roaldz on 2007-12-28
Have you guys seen [this]("http://ubuntuforums.org/showthread.php?t=503928") thread? Could help..

---

### Post by Eddie Hung on 2007-12-28
Ok, I've looked into gksudo and like I said before, it is simply a wrapper around sudo, which only works on the console.

Basically, gksudo runs sudo and intercepts all its input and output. It tells sudo to do replace the prompt that normally appears (i.e. pre-gutsy it used to be just "Password:") with "GNOME_SUDO_PASS" - and when it sees this, it knows that sudo wants a password - and only then does it grab the screen and springs up the input password dialog.

However, sudo only replaces "Password:" when it gets to the pam_unix.so PAM module - and if any other PAM module is used - it goes ahead and displays what that module wants to display (i.e. "Swipe finger on device").

After gksudo runs sudo, it checks almost-immediately whether or not GNOME_SUDO_PASS has appeared - if it hasn't, then it assumes that sudo has already been authenticated, and therefore just sits there and waits for the application that sudo has just run, to exit.

It doesn't take into the scenario that other PAM modules could be before pam_unix, and so even if they fail (i.e. fingerprint doesn't match) - it's still under the assumption that sudo has authenticated, and doesn't respond if GNOME_SUDO_PASS suddenly appears.

However, I see that the sudo version in hardy is 1.6.9p9 - and in this very version, this appears in the [changelog]("http://www.sudo.ws/sudo/stable.html"):
> New passprompt_override option in sudoers to cause sudo's prompt to be used in all cases. Also set when the -p flag is used.

What this implies to me is that sudo will always display GNOME_SUDO_PASS (overriding the "Password:" prompt in this way is invoked by -p flag) regardless of the PAM module - and so gksudo should still spring up and ask for, and supply, a password - whether or not one is required (possible security issue?), and the dialog it displays will also have no indication whether a fingerprint is required, or whatnot - very misleading. And I'm not sure what will happen if you input a password when it is expecting a fingerprint...

But I suppose it's better than it not appearing at all, at least for those that know what's going on...

However, I'm not running hardy - so I can't test this - could someone do the honours?

Fixing gksudo properly would involve implementing PAM directly into gksudo - which would let it work through the PAM chain and display all it's messages correctly, just like GDM and gnome-screensaver do - basically reimplementing the whole of sudo (and sudo doesn't offload it's code into a library that gksudo could link to, either).

However, Ubuntu, and GNOME, are pushing for migration away from gksudo to PolicyKit - and the first implementation is coming in hardy, so IMHO it's not really worth it to fix gksudo, given the amount of work that would be involved. 

EDIT: There are also very good reasons why gksudo should be phased out: [https://blueprints.launchpad.net/ubuntu/+spec/killall-gksudo](https://blueprints.launchpad.net/ubuntu/+spec/killall-gksudo) - the main one being that whenever you run a graphical application using gksudo, your re-running all the GTK code as root.

EDIT2: To be sad and answer my own post again - I can say that I've tried the latest sudo version - v1.6.9p10 - and gksudo is still broke. It still outputs whatever the PAM module wants to say - so maybe I interpreted this new feature wrongly and it isn't meant to fix this at all?

Eddie

---

### Post by yupie on 2008-04-29
I have written a quick-made python script, interacting between sudo and gksu and supporting fprint. You must copy it to /usr/local/bin without an extension.

```
sudo mv ./gksu.py /usr/local/bin/gksu
sudo chmod 755 /usr/local/bin/gksu
sudo apt-get install python-gnome2-extras python-pexpect
```

Only sudo is supported, su will be handled directly by gksu.

---

### Post by ronix on 2008-05-05
> **yupie said:**
> I have written a quick-made python script.

Cool, it works!

---

### Post by ronix on 2008-05-05
I have another issue with fprint, maybe someone has had the same: fprint works fine except when resuming the computer after suspend. Sometimes, but not always, the computer claims, that the aes-device is not ready. After I log in (using my password), I can use fprint_demo without any trouble, so the device works. Maybe the usb-device-resume is delayed after suspend, but this is only a guess. Anybody else having these troubles? Any clues?

Best regards,
Max.

---

### Post by vnieto on 2008-05-05
This python script work, but, Can I use my old gksu script?
In some ocations I can't use sudo gedit for example.
Thanks.

---

### Post by vishalrao on 2008-05-06
FYI, Daniel Drake has published his university project report for fprint: [http://lists.reactivated.net/pipermail/fprint/2008-May/000547.html](http://lists.reactivated.net/pipermail/fprint/2008-May/000547.html) :)

---

### Post by yupie on 2008-05-07
> **vnieto said:**
> This python script work, but, Can I use my old gksu script?
In some ocations I can't use sudo gedit for example.
Thanks.

You can also use "gksu gedit".
If you want to access the original gksu directly, type "/usr/bin/gksu gedit".

---

### Post by cmavr8 on 2008-05-07
Ok, here are my notes:

Case1: Here's the non-commented part of my /etc/pam.d/common-auth:
auth    sufficient    	pam_fprint.so
auth    required      	pam_unix.so nullok_secure
auth    optional	pam_smbpass.so migrate

Like this, no fingerprint is asked when logging in initially.
Sudo in terminal asks for fprint sometimes, but gnome applications get sudo clearance automatically! (and sometimes terminal too)


Case2: If I change the middle line like this:
auth    required      	pam_unix.so try_first_pass nullok_secure

I have: fprint is asked when logging in AND in terminal, fine!
When gnome applications require sudo clearance I think fprint is fine too!

BUT in both common-auth scenarios, [COLOR="Green"]**when unlocking workstation, only my password is accepted (no fprint promtp) AND Network Manager can't get authorized.**[/COLOR]

EDIT:
Thanks for the script.. It works..
Well, not perfectly, as Synaptics asks for normal password... 
Any tips?

EDIT2: Synaptics now asks for fprint.. ok
Main problem remaining: station unlock.

---

### Post by vnieto on 2008-05-10
> **yupie said:**
> You can also use "gksu gedit".
If you want to access the original gksu directly, type "/usr/bin/gksu gedit".

When I use sido gedit, don't work, and in some times update-manager don't work also.

work for synaptic, but only this first time.
Exist any more resent version of yhis script?

---

### Post by vnieto on 2008-05-10
> **vnieto said:**
> When I use sido gedit, don't work, and in some times update-manager don't work also.

work for synaptic, but only this first time.
Exist any more resent version of yhis script?

> **cmavr8 said:**
> Ok, here are my notes:

Case1: Here's the non-commented part of my /etc/pam.d/common-auth:
auth    sufficient    	pam_fprint.so
auth    required      	pam_unix.so nullok_secure
auth    optional	pam_smbpass.so migrate

Like this, no fingerprint is asked when logging in initially.
Sudo in terminal asks for fprint sometimes, but gnome applications get sudo clearance automatically! (and sometimes terminal too)


Case2: If I change the middle line like this:
auth    required      	pam_unix.so try_first_pass nullok_secure

I have: fprint is asked when logging in AND in terminal, fine!
When gnome applications require sudo clearance I think fprint is fine too!

BUT in both common-auth scenarios, [COLOR="Green"]**when unlocking workstation, only my password is accepted (no fprint promtp) AND Network Manager can't get authorized.**[/COLOR]

EDIT:
Thanks for the script.. It works..
Well, not perfectly, as Synaptics asks for normal password... 
Any tips?

EDIT2: Synaptics now asks for fprint.. ok
Main problem remaining: station unlock.

What is the differences between  pam_unix.so nullok_secure and pam_unix.so try_first_pass nullok_secure? I don't Understand you, Can you explain me?

---

### Post by cmavr8 on 2008-05-10
Well, no! Sorry I can't explain, I don't understand it either!

I just try what I find on the web..

Maybe understanding it is a few minutes' studying, but I can't do it right now..

---

### Post by chiccoch on 2008-06-16
wow, now my fingerprint-scanner even works with update-manager and synaptics even with a promt and not just hidden! thanks for the script!

Ubuntu Hardy AMD64 - HP8510w

---

### Post by pibach on 2008-07-08
Works here on Xubuntu Hardy on a x61t.

However:

* I usually unload Kernel module uhci_hcd which supports USB 1.1. This saves me 2-3 Watt because of C3/C4 deeper sleep modes. If uhci_hcd ist loaded, CPU does newer enter C3/4.

* but without uhci_hcd 1.1 fingerprint reader does not work, as it is internally connected by USB 1.1

* the only solution seems to be to load uhci_hcd if gksudo is activated, and unoad it again afterwards

anybody got this working?

---

