---
title: "Firefox in-page search causes GDM to crash?"
date: 2008-10-21
forum: General Help
---

### Post by megadeus on 2008-10-21
This is the weirdest issue I've ever had.

When I type a slash '/' (or use CTRL+F) to search in Firefox 3.0.3 and enter various search strings (originally I thought it was just strings containing the characters 'ddi' but can replicate the error with other strings), Ubuntu logs me out. No confirmation or error message or shutdown, just the screen goes black briefly, the Nvidia logo comes up, then the Gnome Login screen. When I restart Firefox, the "do you want to recover the last session?" message pops up.

I previously thought this problem was due to Gnome Do hogging resources, but I've eliminated that as the cause by replicating the problem with Gnome Do disabled.

It isn't any Firefox add-on, plugin, or theme, I've disabled them all and still get the error. It also happens in Google Chrome, which is weird (to me).

I'm getting frustrated, because the error just spread to the terminal, where I got logged out because I pressed the "down" key instead of the "up" key when trying to recall my last command entered.

I recently updated my kernel, but the error started before that update. I'm using the Nvidia binary drivers through the EnvyNG tool, if that might be the cause of the problem. I can't remember if the problem started before I started using EnvyNG or not.

Originally posted at the [Livejournal Ubuntu_users group]("http://community.livejournal.com/ubuntu_users/352179.html"), but I figured the more eyes I had on this problem, the better.

---

