---
title: "Update warning - what now ?"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by pacman5 on 2009-05-03
I'm using Ubuntu 8.4 Hardy Heron.

This morning I got the little sign at the top right of my screen telling me that updates were available. When I tried to download and install I got the message "You are about to install software that can't be authenticated ! Doing this could allow a malicious individual to damage or take control of your system". There follows a window containing what seem to be 3 categories: NOT AUTHENTICATED,To be upgraded, To be installed.

There are no options that I can see in this dialog which allow me to reject the software that cannot be authenticated. So, as far as I can see, by upgrading my Ubuntu 8.04 Hardy Heron I will compromise my system.

Does anyone here know how to deal with this ?

P.S. An update to this: it seems that the problem might have to do with attempts this morning to access Medibuntu so as to download and install Google Earth. Those attempts didn't seem to work (it threw up a message saying that a public key was needed but, of course, the message didn't say where to find that public key or how to implement it). I now unchecked those Medibuntu items from the download list and the system update works. Having solved my problem myself I'd like to delete this message from the forum but cannot see how to do it.

Now to try to have another go at adding Medibuntu to my repositories.

---

### Post by svivian on 2009-05-03
In reality the 'not authenticated' message isn't a risk if you're using a source that you trust (e.g. Google).

But to get rid of the message, you need to find the public key file, which will be on the server that you're getting the packages from. In your case I'm guessing it's [http://packages.medibuntu.org/](http://packages.medibuntu.org/)

There will be a .pgp file somewhere, you need to save that as a file somewhere on your system then go to Synaptic Package Manager > Settings > Repositories > Authentication and import the key file you downloaded.

---

### Post by drs305 on 2009-05-03
If you get a specific message saying you don't have the proper key you can post the message and we can show you how to get the public key. 

If you just want to get on with the upgrade, so into Synaptic and disable the third-party repositories (Settings, Repositories, Third-party), leaving only the official repositories. You should then stop receiving the security messages.


**[COLOR="DarkRed"]Update:[/COLOR]** I see you updated your message and it *was* medibuntu. The message should have provided a code. Medibuntu now provides a universal set of commands to import the correct keys. Just run the following:
```

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

```

It's from here: [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by pacman5 on 2009-05-10
Thank you both for your tips/leads on this issue. I've been "out of town" for a while but will now have another try at this using your ideas and report back.

Greatly appreciate the support from this community.

---

