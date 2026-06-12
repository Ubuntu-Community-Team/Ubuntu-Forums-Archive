---
title: "[SOLVED] keyring manager"
date: 2008-11-09
forum: General Help
---

### Post by daz4126 on 2008-11-09
When I log in I always get a message that the network manager needs the keyring manager password before it connects to wifi.

Is there a way for this to happen automatically (it did on hardy)?

..and does anybody know how to change the keyring password? I can't find a way to do it anywhere!

Thanks,

DAZ

---

### Post by daz4126 on 2008-11-12
anyone??

---

### Post by john183 on 2008-11-12
Check out this tutorial over at Ubuntu-tutorials.com :
[http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/](http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/)

I cannot say that i have tried it myself, but i do know a few who have said that it worked just fine for them.

---

### Post by SamNSane on 2008-11-12
> **daz4126 said:**
> When I log in I always get a message that the network manager needs the keyring manager password before it connects to wifi.

Is there a way for this to happen automatically (it did on hardy)?

..and does anybody know how to change the keyring password? I can't find a way to do it anywhere!

Thanks,

DAZ

I found the change in the way this is handled between Hardy and Intrepid to be kind of odd. You can find Encryption / Keyring applets in more than one place in both operating systems. But for this particular purpose:

In Hardy, you go into System / Preferences / Encryption and Keyrings.

In Intrepid, you go into Accessories and click on the applet. (Sorry, not sure about the exact name, because I went back from Intrepid to Hardy.)

Anyway, IIRC on the first tab (Password Keyrings, I think) you'll see a list that probably just contains one entry - "login Automatically unlocked when user logs in" or something along those lines. Select it.

Now in Hardy, there's a "Change Unlock Password" button that becomes available at this point. However, I think Intrepid makes you right-click on that keyring to get to the dialog you need for changing the unlock password. You may have to explore a little. I remember thinking it wasn't very intuitive.

Here's the thing. When you set up your original password for the user account, I think that also sets this keyring password. From then on, when you change the user account password you have to come into this applet and change the unlock password, too. If you do that, then the wireless connection app won't ask you to provide a password every time you log on and start to connect to your wireless network.

At least that's the way it has worked for me. If you're using autologin, then I'm not sure just what you have to do to deal with this. This has been kind of handled oddly and differently as versions of Ubuntu come and go. I remember having to install a utility on older versions of Ubuntu that would automatically synchronize these functions.

At any rate, I've been able to synchronize so that I don't get the prompt in both Hardy and Intrepid without understanding much about it, so you should be able to get it done, too! Just wander around in the mental darkness right-clicking and selecting options.

;)

I should point out that the network manager applet in Intrepid is MUCH improved over the same dingus under Hardy. Now that I'm back on Hardy I finally axed its stupid little network manager and replaced it with wicd, which doesn't put me through any of this. The main reason that I like wicd more under Hardy is the way it handles multiple connections. But the network manager on Intrepid does this pretty well, too.

OK, now that I've rattled along for so long, maybe someone who actually knows what s/he's doing will come along and give you a definitive answer!

Hey, cool! While I was digressing, someone who knows more ALREADY came along! I'm going to go look at that tutorial and see if I had any idea at all what I was talking about!

---

### Post by daz4126 on 2008-11-12
Thanks guys!

SamNSane - your method worked. You were dead right that it is totally not intuitive, but by clicking on nearly everything and changing all prompts for passwords to my user login, I got it to work. I guess that the password on here has to be the same as your login password for this to work? I changed my login password when I upgraded to Ibex, so that would explain it. If that is the case then there should be a prompt when you change your login password that asks if you want to also update your keyring password too.

Jonathon - Thanks for the link, I didn't actually have to use this method, but that looks like a useful site all the same.

cheers again,

DAZ

---

### Post by SamNSane on 2008-11-13
> **daz4126 said:**
> Thanks guys!

SamNSane - your method worked. You were dead right that it is totally not intuitive, but by clicking on nearly everything and changing all prompts for passwords to my user login, I got it to work. I guess that the password on here has to be the same as your login password for this to work? I changed my login password when I upgraded to Ibex, so that would explain it. If that is the case then there should be a prompt when you change your login password that asks if you want to also update your keyring password too.

Jonathon - Thanks for the link, I didn't actually have to use this method, but that looks like a useful site all the same.

cheers again,

DAZ

I'm glad to see that it worked out for you. I went that way because I like to take the least "invasive" course in solving a problem. So my natural path is to just try to deal with the distro using the tools that come with it, rather than uninstalling this package and installing that package.

The way it has worked for me is that I just go change the keyring password immediately after I change the user password. That way I don't get the gnome-keyring prompt. However, in Hardy the little network-manager applet is just plain old brain-dead. It works okay for people who always get their IP address assignments via DHCP, but my laptops travel to a number of places where I have to use fixed IP addresses and alternate DNS settings. The network manager in Intrepid is HUGELY improved, and it can handle saving lots of different network profiles.

But in Hardy, I've broken my own rule about not being invasive. I use wicd to replace the network-manager, and I'm happy with that.

---

### Post by Gumm on 2008-11-14
> **SamNSane said:**
> 

Here's the thing. When you set up your original password for the user account, I think that also sets this keyring password. From then on, when you change the user account password you have to come into this applet and change the unlock password, too. If you do that, then the wireless connection app won't ask you to provide a password every time you log on and start to connect to your wireless network.



Thanks SamNSane. This seems to point me in a direction to solve my own woes. I have a Dell M6300, and now, for the first time since I got it a couple of years ago, I managed to get the fingerprint scanner working (yeah-yeah - I know its a gimmick, but all the same :)).

So I can log in by scanning my finger, but (and I suspect it is because the biometric stuff is still experimental and seems to be under heavy development) I can not set the keyring manager's "Unlock Password" to use this.

So for now (until I either run out of enthusiasm for biometrics, or until that project becomes more mature and integrated) I seem to be stuck with having to enter my normal password to give network manager access to the keyring.

On a further note, I tried the tut below:

> Check out this tutorial over at Ubuntu-tutorials.com :
[http://ubuntu-tutorials.com/2007/07/...g-pam-keyring/](http://ubuntu-tutorials.com/2007/07/...g-pam-keyring/)

Again I think this has to do with using the biometric log-in, but following this tut left me stranded outside GTK, and I had to use the console to reverse out of the changes proposed by this tut...

---

### Post by SamNSane on 2008-11-14
> So I can log in by scanning my finger, but (and I suspect it is because the biometric stuff is still experimental and seems to be under heavy development) I can not set the keyring manager's "Unlock Password" to use this.

Sounds like you need to find a way to give the keyring manager "the finger" -- BWA-HA-HA-HA. (Sorry. Sometimes my mind just works that way.)

> So for now (until I either run out of enthusiasm for biometrics, or until that project becomes more mature and integrated) I seem to be stuck with having to enter my normal password to give network manager access to the keyring.

Unless you replace network manager with something like wicd. Wicd doesn't use the gnome-keyring thingy. If you go to the Web site for wicd you'll find very clear instructions on installing it in Ubuntu. You do it by enabling a repository and the associated certificate in Synaptic, reloading, and then installing wicd from the new repository. The process will automatically remove network-manager.

Now, mind you, I'm not necessarily recommending that you do this. Network-manager, for all its shortcomings in Hardy (It's far better in Intrepid.) is well-integrated into the gnome desktop system. You'll notice that when you go to change network settings with network-manager you have to unlock those settings with a password. There's no such protection with wicd. It's pretty obvious that there are situations where this would not be a good thing. But it's also pretty obvious that at least some of us don't really need that particular protection. My workstations only get used by me, and they get locked when I walk away from them.

On the other hand, it's possible that the network-manager integration with gnome-keyring may provide protections from other possibilities (changes in network settings being made through the manager by malware? no idea whether or not this could happen).

Anyway, the limitations in the Hardy version network-manager's ability to deal with a mix of fixed IP addresses and multiple network profiles makes its elimination from a Hardy installation almost mandatory for me. If I were running Intrepid, I'd just stick with its version of network-manager and just deal with the synchronization issue. (But I don't have biometrics, either.) I used Intrepid for a couple of weeks and found its network-manager to be just fine.

Good luck at finding a solution. Maybe someone needs to write a gnome applet called ring-finger?

;)

---

### Post by daz4126 on 2008-11-16
Thanks again SamNSane. I too like to use the path of least resistance and avoid installing new programs. I didn't have any issues with the network manager on Hardy, but hardly every use the laptop outside of my house anyway. It's good to know that the one in Intrepid is better though as I've upgraded to Intrepid on all machines now.

cheers,

DAZ

---

