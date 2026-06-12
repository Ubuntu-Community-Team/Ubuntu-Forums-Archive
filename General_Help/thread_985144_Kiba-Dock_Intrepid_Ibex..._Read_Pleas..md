---
title: "Kiba-Dock Intrepid Ibex... Read Pleas."
date: 2008-11-17
forum: General Help
---

### Post by saggitheman on 2008-11-17
Hi guys.

I'v tryed to install kiba-dock... the installation went great, but when i type kiba-dock in terminal, I get this message...
What to do? Should  install the global plugins? Can't find them... Help pleas


'root@Dell:/home/aleksander# kiba-dock

** (kiba-dock:26603): WARNING **: Error (plugin-loader.c @ line 665):
Failed to open Plugin Directory '/usr/local/lib/kiba-dock/global_plugins': Error opening directory '/usr/local/lib/kiba-dock/global_plugins': No such file or directory

For a core dump, run kiba-dock with --g-fatal-warnings

---

### Post by binbash on 2008-11-17
is this a svn build?What was the order you followed compiling?(example : kiba-dock first dbus plugin second etc)Did you install all Deps?

PS : BTW kiba-dock latest svn works on ibex, i was using it.

---

### Post by loomsen on 2008-11-17
> **saggitheman said:**
> 
root@Dell:/home/aleksander# kiba-dock


Not for all the tea in china you should act as root from this workdir.

Obv you don't care too much about users permissions, so that most likely your permissions are messed up anyway.
If you think this might apply to you, either ask google how to fix permissions on a users account, or create a new account.

If you're using amd64, you can grab *.deb pkges I build. See the link in my sig.

---

