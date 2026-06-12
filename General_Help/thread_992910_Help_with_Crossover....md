---
title: "Help with Crossover..."
date: 2008-11-25
forum: General Help
---

### Post by Doebringer on 2008-11-25
Crossover support gave me a generic answer to my query that hasn't really helped me at all.

I got the lame duck challenge free registration for crossover in the hopes that it would enable me to completely leave windows behind (a few games are all that binds me to windows at this point) and though I had some difficulty at first installing the software, I've got it now.

My trouble is this: The download itself is a 'demo' version, and the full version must be unlocked by entering your email and registration code. When I do this, I get a couple of strange errors, which I have transcribed below:

"Automatic registration failed when creating a temporary bottle: Error
executing '"/opt/cxgames/bin/cxbottle" --creat --scope private --bottle
"unlockbottle-4" --install':

wine: Unhandled page fault on read access to 0x00000200 at address
0xb7f27fed (thread 0027), starting debugger...
setup:error: 'rundll32 DefaultInstall crossover.inf' failed
wine: Unhandled page fault on read access to 0x00000200 at address
0xb7fe2fed (thread 0020), starting debugger...
setup:error: 'rundll32 DefaultInstall crossover.inf' failed
cxbottle:error: unable to create the 'unlockbottle-4' bottle in
'/root/.cxgamers/unlockbottle-4'

And then it tells me to contact support if the problem persists. This is the response I got from their support person:

"Make sure you're using a regular user account to register Crossover with, not the root account. That unlockbottle-4 error is usually caused by new security restrictions present in Ubuntu 8.10."

The problem is, that I *am* using my regular user account for the installation. At least... I think I am... I only have the one account (the one it asked me to make upon initial installation of ubuntu).

Any assistance would be, in a word, awesome.

---

### Post by john.nicholls on 2008-11-25
> **Doebringer said:**
> 
I got the lame duck challenge free registration for crossover in the hopes that it would enable me to completely leave windows behind (a few games are all that binds me to windows at this point) and though I had some difficulty at first installing the software, I've got it now.

My trouble is this: The download itself is a 'demo' version, and the full version must be unlocked by entering your email and registration code. 

My download was the full version. The instructions I got from Codeweavers were as follows:


"Go to [www.codeweavers.com](www.codeweavers.com)
<click> Log-in
<click> Returning customer
<enter> Username =  xxx
<enter> Password =  yyy

Now, <click> My Account (upper right hand corner) <click> My Downloads (fifth link in box on left)

Here is where you will find the download."

Could you try this and see what happens?

---

### Post by Doebringer on 2008-11-26
Thanks for the reply - I do have access to the full version download of Crossover Pro, but the one I'm having trouble with is Crossover Games. I've been all over my account profile on the crossover website, and the only download I can find for crossover games is for the demo version.

I've thought about trying to install my games using crossover pro, but they aren't supported with that version of crossover, whereas they *are* supported with the crossover games edition.

---

