---
title: "Fingerprint reader"
date: 2018-08-03
forum: Hardware
---

### Post by s2maschmeyer on 2018-08-03
Hi,
I have a PQI My Lockey which is not compatible with Linux (uses Validity/Synaptics technology), exclusively work with Windows.
I would like to know where I can find a list of current consumer (small USB) fingerprint readers that are compatible. 
I don't mind if it uses an older technology but I would like it to be a small form-factor (like a mouse dongle) and affordable (I am a poor university student). 
I am often working around strangers, in the computer labs, entering passwords. 
While I trust the people around me, I would prefer to use my finger.

Please advise

---

### Post by TheFu on 2018-08-03
If you care about security, don't use fingerprints for security.
[http://fortune.com/2016/02/24/fingerprint-spoofing-easy/](http://fortune.com/2016/02/24/fingerprint-spoofing-easy/)

[https://www.youtube.com/watch?v=Ta-aLSHSKC4](https://www.youtube.com/watch?v=Ta-aLSHSKC4) go to 14:48 and watch how to crack fingerprint readers. It is a typical Defcon video (cussing), so don't let the kids be in the room when you watch, but the security info is solid.   
22 minutes in, it describes in detail how biometrics work.   
27 minutes in he discusses credential revocation difficulties.

---

### Post by kurt18947 on 2018-08-04
I'm not security expert but I've read/heard this and it makes sense. If using biometrics as a password or key, that information is being stored in a database somewhere. Databases are targets and a database storing I.D.s and biometric information would be a high value target. It's easy to change passwords or keys if a database is hacked. Fingerprints and retinas? Not so much.

---

### Post by s2maschmeyer on 2018-08-05
There is a lot of fear out there. The bio-metrics is not stored in a cloud, the data is stored on a chip, located on the motherboard called the TPM (at least that is the method used today, older fingerprint readers often included their own version of a TPM, TPM v2 is an industry standard). On a fingerprint reader, not the whole fingerprint is stored (useless if you want to frame someone), only a few random locations which are then encrypted and stored on the MOBO chip. Windows Hello (or Windows 7 login) for instance, only requests if the information is correct from the TPM, gets a yes or no response from the TPM. Linux seems to only use older fingerprint readers that do not utilize the TPM on the motherboard (speculation). The passwords, could be stored on a cloud, but generally in a local storage keyring (i.e. Google Chrome could be setup to ask you to type in a password to unlock all passwords). While fingerprint readers can be fooled, the PQI myLockey also detects heart beat (breath sensing), it would be more trouble than it is worth for a student laptop. I just don't want to type in my password/pin while in a public place for someone walking by to view, even if I have different passwords for different accounts. As, remembering a password someone typed next to you is easier.

---

### Post by kurt18947 on 2018-08-24
I was speaking more to door locks and other physical access devices than laptops. I'm not at all familiar with TPM ver. x so don't know how strong they are. If someone stole your laptop, could they harvest the information stored there? Maybe use a password manager? That way if someone were able to figure out what you were typing, they'd know only your password manager password, not your various account passwords.  I think they'd have to get possession of your laptop to get the various passwords stored in your password manager. Don't store your password manager info "in the cloud". Encrypt some or all of the hard drive and you've created another stumbling block. I"m no expert in this stuff but read quite a lot and pay attention to what seems to make sense.

---

### Post by TheFu on 2018-08-24
Spoofing fingerprints is one of the easier biometrics to trick.  Security professionals recommend against using any biometric as a first-level authentication method.  Requiring both something you know, a password, and something you have (some sort of crypto-device/key), is still the best solution for most people.  I don't consider any PIN to be secure.

Revocation of a finger print is a little more pain than I'd like.  Might I suggest using a USB key with a certificate for the 2nd factor instead?  Grub and LUKS can work with those today.  Keeping my fingers is a personal priority.  ;)

---

### Post by Sweetdulldaffodil on 2018-12-15
> **s2maschmeyer said:**
> There is a lot of fear out there. The biometrics is not stored in a cloud, the data is stored on a chip,
That's a lot of assumption. You don't know that!
Or actually, I do know that's not true and I'm sure you do know too (although you might not realise it).

For instance, it would be insanely naive to assume your accumulated fingerprints made on any device (phones/keyboards/entries) wouldn't be stored somewhere in a cloud, either by evil manufactures, or manufactures forced to do so by evil governments.
Also, your fingerprint is blunt clearly stored in the cloud by the government when you travel and pass customs or in many countries when you acquire a travel document (passport/ID/driver licence).

Fact is, wherever you are, wherever you go, you leave a mass amount of fingerprints behind and you should assume they're in the open as long as you can't prove otherwise.

Fingerprints are UserID's, not Passwords!

---

### Post by lseifert2 on 2019-12-03
> **s2maschmeyer said:**
> Hi,
I have a PQI My Lockey which is not compatible with Linux (uses Validity/Synaptics technology), exclusively work with Windows.
I would like to know where I can find a list of current consumer (small USB) fingerprint readers that are compatible. 
I don't mind if it uses an older technology but I would like it to be a small form-factor (like a mouse dongle) and affordable (I am a poor university student). 
I am often working around strangers, in the computer labs, entering passwords. 
While I trust the people around me, I would prefer to use my finger.

Please advise

    To answer the question, with-holding my opinion until later, yes, anything that works with fprint, according to the project web page in git lab the project has not been updated in 4 years, so this may or may not work with later versions of Linux, specifically Ubuntu.  A device known to work with this library is the u.are.u 4500 or 4000 series, they can be found new and used on Amazon and Ebay. According to the Ubuntu release page [disco (19.04)]("https://packages.ubuntu.com/disco/libpam-fprintd")[COLOR=#333333][FONT=Ubuntu] (admin): PAM module for fingerprint authentication through fprintd, the module is still available and is included in the 19.04 and will likely be included in 19.10 as well, which means it is still supported, since it is a PAM module it can be integrated easily into the authentication systems easily..[/FONT][/COLOR]  Since the original question was submitted by a student, using this, while a security risk, might not be a huge risk, unless the college has an active Red Team Security group. ( Red Teams are white hat hackers, however, it would be illegal, and also not "white hat" if they circumvented the security on your system. ). Unfortunately, I have not found a cool key style fingerprint reader that anyone is willing to say works, they might exist, I just don't want to dedicate my life to looking for the perfect one. ( feel free to add comments with a better device if your aware of any ) 

    Another good single factor authentication system is an authentication key like the Google titan, or the yubico security key, however, if you leave the key in or someone gets the key they have complete access to your system as a single factor, putting in a simple password and adding a second factor isn't terribly difficult and would greatly improve your security.  

To add a security key, the non-bluetooth Google key works this way as well.
Add the device in udev config
[https://support.google.com/titansecuritykey/answer/9148044?hl=en](https://support.google.com/titansecuritykey/answer/9148044?hl=en)

Then follow this guide[URL="https://support.yubico.com/support/solutions/articles/15000011356-ubuntu-linux-login-guide-u2f"]
https://support.yubico.com/support/solutions/articles/15000011356-ubuntu-linux-login-guide-u2f[/URL]

Then make sure that you add the second factor to the PAM configs you want a second factor on, be sure to follow the methods for testing so you don't lock yourself out.  Get the command line working first, that way if you screw up the GDM you can always login to the command line on another window and fix it. 

I also use this as a backup authentication factor
[https://www.digitalocean.com/community/tutorials/how-to-set-up-multi-factor-authentication-for-ssh-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-multi-factor-authentication-for-ssh-on-ubuntu-16-04)

Then: 
sudo vim /etc/pam.d/login
# Standard Un*x authentication.
@include common-auth
auth       sufficient pam_u2f.so
auth       sufficient pam_google_authenticator.so


Do the same for /etc/pam.d/sudo ,/etc/pam.d/sshd, /etc/pam.d/gdm-password and any further pam file  You want to prevent all standard entry points. 

Untested: To add a second key, which I am working on getting now, you would replace > with >> so that the initial isn't overwritten if it works like any other fingerprint system.

    If the person was a security student, you would already know that you shouldn't use a single factor for authentication in an un-trusted space, and wouldn't be asking the question in the first place.  In fact, the more REQUIRED methods the better.  My opinion is that you should have at least two if not 3+ factors. This means, something you know, a password, then a "something you have" which should have a backup in case you lose the "something you have", and a something you are, which ideally would also have a backup, in-case your something yo are gets cut out or off. ( some finger print readers will not properly read your fingers if you get your fingers seared by accidentally touching a frying pan ).  This is the reason that you should have a backup.  Lastly, in the ideal security setup, you also have encryption on your drive, a firewall enabled to block both incoming AND outgoing ( iptables -p INPUT DROP; iptables -p OUTPUT DROP; iptables -p FORWARD DROP, and then put your exceptions in ).  Securing your workstation is actually the topic of an entirely different and probably multiple forums.

-----------------------EDIT---------------------------

sufficient worked pretty much the opposite from intended, it is a little strange because I tested this on my workstation and it worked the way I expected, but when I came back to it, I was able to bypas the authenticator method by just hitting enter,  Iso at the moment there isn't a backup method without using more advaced pam.d configations.  For now I am just going to pu the authenticator on network connections, and key on local logins, and I advise to do the same, I have a new key arriving monday which I will post the result whether or not I was able to add it as a backup second factor..

If a sufficient module succeeds, it is enough to satisfy the
        requirements of sufficient modules in that realm for use of the
        service, and modules below it that are also listed as &#8216;sufficient&#8217;
        are not invoked. If it fails, the operation fails unless a module
        invoked after it succeeds. Important to note is that if a &#8216;required&#8217;
        module fails before a &#8216;sufficient&#8217; one succeeds, the operation will
        fail anyway, ignoring the status of any &#8216;sufficient&#8217; modules.

---

