---
title: "Im back wiht Ubuntu 64 bit. need help"
date: 2008-10-02
forum: General Help
---

### Post by Vertoxic on 2008-10-02
Hi guys i just got Ubuntu 6 bit4 installed on my new laptop m-6864 Gateway intel 2.0 4 gig ram ATI 2600HD 
need to install flash wich dont work... cant watch youtube :(
i kinda new to this so plz help me thx!
i tried 

sudo ./GetFlash

toliy@toliy-laptop:~$ sudo ./GetFlash
sudo: ./GetFlash: command not found

dont know what it is do i need to get some admin option or something i just installed this like 5 min ago thx guys!!!!

---

### Post by lonniehenry on 2008-10-02
What version of Ubuntu did you install? If it were Hardy 8.04 then [http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy) will help get you started.

---

### Post by Vertoxic on 2008-10-02
yes i got the newest version from their website just a few min ago :) 
64 bit

---

### Post by haydnc on 2008-10-02
I have not yet had time to play with the 64 bit variety but I'd be surprised if you couldn't just click:

Programs - Add and Remove Programs (I think that's what its called)


Do a search for flash and install it.

Maybe.

Sorry for the horribly non-specific response. :p

---

### Post by Vertoxic on 2008-10-02
> **lonniehenry said:**
> What version of Ubuntu did you install? If it were Hardy 8.04 then [http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy) will help get you started.
im sorry that dont tell me anything to much info i just had one question about flash install!!!!!

---

### Post by haydnc on 2008-10-02
On consideration you could probably also try opening up a Terminal and using this:

```
sudo apt-get install ubuntu-restricted-extras
```

I know that would get you flash on the 32 bit version of Ubuntu and everyone keeps telling me that they've fixed up the 64 bit version so that all that kind of thing is working.

---

### Post by Vertoxic on 2008-10-02
whats this? how do i fix this?

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

this happend while i was trying to download flash from "add/remove"

---

### Post by Vertoxic on 2008-10-02
plz try to help me thx

---

### Post by Vertoxic on 2008-10-02
if i go back to ubuntu 32 bit wich is much easier!!! 
 will it read my 4 gig of ram or no?

---

### Post by haydnc on 2008-10-02
When you run the Add / Remove programs it basically runs a copy of the Synaptic Package Manager - the standard interface for adding and removing all programs in Ubuntu.

I might be wrong, but from memory that message you're seeing comes up when a copy of Synaptic is working on something (usually the update manager) and you try to open another copy of Synaptic.

You'll probably find that it'll start working again on its own in a few minutes.

Someone else might be able to give you confirmation of that. Unfortunately I'm not near my Ubuntu machine at the moment so I can't test/sugget any other work arounds. Sorry.

---

### Post by Kilz on 2008-10-03
> **Vertoxic said:**
> Hi guys i just got Ubuntu 6 bit4 installed on my new laptop m-6864 Gateway intel 2.0 4 gig ram ATI 2600HD 
need to install flash wich dont work... cant watch youtube :(
i kinda new to this so plz help me thx!
i tried 

sudo ./GetFlash

toliy@toliy-laptop:~$ sudo ./GetFlash
sudo: ./GetFlash: command not found

dont know what it is do i need to get some admin option or something i just installed this like 5 min ago thx guys!!!!

The command here is to run the automated install script.

> **Vertoxic said:**
> yes i got the newest version from their website just a few min ago :) 
64 bit

Indicating he is running Hardy Heron 8.04.

But if we take a look at [the Flash Sticky]("http://ubuntuforums.org/showthread.php?t=772490") we see THERE IS NO SCRIPT FOR HARDY. In fact in the Hardy section
**[COLOR="Red"]DO Not[/COLOR]** install the scripts below. Run all the commands above again. The script will only make things worse. 

Then we see the **[SIZE="4"][COLOR="Red"]Big Bold Red[/COLOR][/SIZE]** letters suggesting exactly what to do to get help
**[SIZE="4"][COLOR="Red"]How to get help (Please Read Before Making a Post)[/COLOR][/SIZE]**
below that is 
When you make a post, make in in this thread.
Incude some info
Report the bug on launchpad
Then the kicker.
**[COLOR="Red"]Hardy users should not install the automated script or try other methods.[/COLOR]**

Riggght its a flash problem....

I will say no more. Im sure if I do I will get a warning for something. 	:-#

---

