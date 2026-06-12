---
title: "Bitlbee registration"
date: 2008-10-31
forum: General Help
---

### Post by m0lo on 2008-10-31
I'm trying to get bitlbee wokring and I'm following this guide:
[http://en.linuxreviews.org/Bitlbee](http://en.linuxreviews.org/Bitlbee)

and when I come to this step that says:
"Remember to save your settings (if save_on_quit is set to false)!"
I get "08:32 <@root> Please create an account first"

I have created an account (account add msn [email]myusername@provider.com[/email] mypassword).
What could be the problem? When i typed in account add msn [email]myusername@provider.com[/email] mypassword it say "account successfully added".
Help a n00b :(

---

### Post by FutanariKitty on 2008-10-31
Well, it has been a bit of time since I've used bitlbee (I do so love that bit of software though...), I might be able to help. That guide you're looking at seems awfully extensive (not a bad thing, really).

Anyway, are you running bitlbee yourself, or are you connecting to a public server? You really should run it locally, unless you absolutely need it off-site for some reason.

I think all you're attempting to do is save your information before actually creating your profile. Quite simple to rectify. First, set your password for your profile:
```
register password
```
From now on, you'll need to identify yourself when you start your IRC client to reload your profile:
```
identify password
```
Then, add the accounts as listed in your guide. I'll not reiterate that simply because you already know that step. Once all your account information has been entered, you simply start up your connections with
```
account on
```
And there you are!

Now, this would be a good time to save your data with the ```
save
```command.

From now on, when you use the identify command, your accounts will automatically connect. Hope this helps!

---

### Post by m0lo on 2008-10-31
Thanks for your kind and fast reply! How do I run it locally?

---

### Post by FutanariKitty on 2008-11-02
Sorry about the slow reply...you know how the holidays are. There was much drinking, partying, dancing, etc....then the inevitable hangovers began...

Back on topic. Quite simple, just install bitlbee from the repositories.
```
sudo aptitude install bitlbee
```
should do the trick (or install using Synaptic, your choice). I'm still assuming you do have it set up to run on your home computer, but if I'm wrong, that will drop the package in place. Good luck!

---

