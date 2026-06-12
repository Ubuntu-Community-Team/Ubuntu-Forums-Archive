---
title: "[SOLVED] nm-applet problem"
date: 2008-10-06
forum: General Help
---

### Post by soho2014 on 2008-10-06
I am a newbie, so I didn't understand the solution that I read about here, but I thought that maybe someone could let me know if it is safe to remove the application known as: "nm-applet".

The problem is that it gives me the following message every time I log in, asking me for my password:

"The application 'nm-applet' ( /usr/bin/nm-applet) wants to access to the default keyring, but it is locked"   

such that I have to supply a password, which I've somehow made different as my log in password.  I don't see any extra security advantage to this step ,and I was wondering if I can just scrap the nm-applet without damaging my system.

---

### Post by OutOfReach on 2008-10-06
Well, nm-applet is **N**etwork**M**anager-applet so removing that would take away internet access, since nm-applet is used to access the internet. You can install wicd ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)) and see if you have better luck with that (also a network manager).

---

### Post by aysiu on 2008-10-06
Just as a follow-up, though, if you install WICD, it'll automatically remove Network Manager (which is fine, but I just wanted to let you know it would be removed).

---

### Post by soho2014 on 2008-10-06
> **OutOfReach said:**
> Well, nm-applet is **N**etwork**M**anager-applet so removing that would take away internet access, since nm-applet is used to access the internet. You can install wicd ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)) and see if you have better luck with that (also a network manager).

OK, I guessed that nm might mean network manager, and I was afraid of this very problem.  Is there anyway such that I might be able to change the password that I've somehow supplied to the nm-applet?  I've looked everywhere, and I don't see any easy way to change it.

---

### Post by soho2014 on 2008-10-06
When I look around there in the network manager though, the only password that I see in there is my WEP security password to get onto my wireless network.  I don't see the place where I can change my nm-applet password, unfortunately.

---

### Post by haydnc on 2008-10-06
Hi soho2014..

From reading what you put in your initial post I believe you might be looking for the wrong thing.

The password that you're entering is actually nothing to do with NM-applet, it is actually the password for your default keyring.

The keyring is used to store the passwords you type on your computer so that they're all in a single secure location. (More or less).

Have a look under System - Preferences or System - Administration and see if you can find the keyring manager. (I can't remember where it is and I don't have Ubuntu access at the moment.) You should be able to access the keyring and either remove the entry caused by NM-applet or (possibly) set things up so that NM-applet doesn't always have to ask to access the keyring.

Alternatively have a bit of a search around and see if there is some way to auto-access the keyring on your regular login. It's less secure but it wouldn't surprise me if someone had asked how to do it before and probably figured out a way.

---

### Post by soho2014 on 2008-10-06
I think that I've figured out my answer.  I didn't understand before that my login password [Prefs>>Encryption + Keyrings] is not the same thing as my user password that I supply to login to Ubuntu.

When I changed the login password to the same one  as my user password the problem has disappeared, and finally nm-manage doesn't ask me for my password every time!:guitar:

---

### Post by soho2014 on 2008-10-06
> **haydnc said:**
> Hi soho2014..

From reading what you put in your initial post I believe you might be looking for the wrong thing.

The password that you're entering is actually nothing to do with NM-applet, it is actually the password for your default keyring.

The keyring is used to store the passwords you type on your computer so that they're all in a single secure location. (More or less).

Have a look under System - Preferences or System - Administration and see if you can find the keyring manager. (I can't remember where it is and I don't have Ubuntu access at the moment.) You should be able to access the keyring and either remove the entry caused by NM-applet or (possibly) set things up so that NM-applet doesn't always have to ask to access the keyring.

Alternatively have a bit of a search around and see if there is some way to auto-access the keyring on your regular login. It's less secure but it wouldn't surprise me if someone had asked how to do it before and probably figured out a way.

Yes, I figured this out myself minutes before you replied, but thank you very much for taking the time to respond and help me!  It took me the better part of the evening to figure this out, but at least I won't forget it!  It seems that as long as I keep the password for my keyring as the same password as my user password, then the network manager won't bug me for hte keyring password.

---

### Post by mariane_08 on 2008-12-05
> **soho2014 said:**
> Yes, I figured this out myself minutes before you replied, but thank you very much for taking the time to respond and help me!  It took me the better part of the evening to figure this out, but at least I won't forget it!  It seems that as long as I keep the password for my keyring as the same password as my user password, then the network manager won't bug me for hte keyring password.

I'm having this same problem at bootup. Every time nm-aplet is demanding "access to the default keyring but is locked" I have changed my passwords so they are the same. 

I've looked in system>preferences>Encryption and Keyrings and am wondering if there is something else I can change or set so this stops happening.

Please help if you have any ideas!!!
Thanks

---

### Post by soho2014 on 2008-12-05
> **mariane_08 said:**
> I'm having this same problem at bootup. Every time nm-aplet is demanding "access to the default keyring but is locked" I have changed my passwords so they are the same. 

I've looked in system>preferences>Encryption and Keyrings and am wondering if there is something else I can change or set so this stops happening.

Please help if you have any ideas!!!
Thanks

I would try just closing that little applet window and not even trying to give it any info.

---

