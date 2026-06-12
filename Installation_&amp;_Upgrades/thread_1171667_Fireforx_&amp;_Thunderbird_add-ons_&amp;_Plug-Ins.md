---
title: "Fireforx &amp; Thunderbird add-ons &amp; Plug-Ins"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by joelop on 2009-05-27
Hi All,

I'm moving from Win XP to Ubuntu and I have a doubt now. I have a very customized Firefox and Thunderbird and I'd like to know if there's any tool that I could use to save this settings in Win to make it work in Ubuntu.

Is there an easy way for the migration of these program's customizations?

---

### Post by albinootje on 2009-05-27
> **joelop said:**
>  Is there an easy way for the migration of these program's customizations?

You can simply copy the whole profile directory, and use that in both Thunderbird and Firefox.

See here : [http://support.mozilla.com/en-US/kb/Profiles](http://support.mozilla.com/en-US/kb/Profiles) (choose Linux or Windows).

After finding the profile itself, and copying it, start Firefox with the Profile Manager in a terminal :
```

firefox -P

```
Create a new profile, and then make sure that it will use your copied profile directory as directory.

---

### Post by florus on 2009-05-27
You must uninstall your add-ons before copying your profile. Add-ons are compiled differently for Linux and the Windows ones will not work.

---

### Post by presence1960 on 2009-05-27
also the command to open profile manager is>  firefox -profilemanager and > thunderbird -profilemanager

I copied my profile folders for FF & TB over from windows. The addons that didn't work I just removed from ubuntu and added the ones for Linux.

---

### Post by albinootje on 2009-05-27
> **presence1960 said:**
> also the command to open profile manager is

Are you telling me that I'm -not- successfully using "firefox -P" since years ? Try/test it yourself.

---

### Post by presence1960 on 2009-05-27
> **albinootje said:**
> Are you telling me that I'm -not- successfully using "firefox -P" since years ? Try/test it yourself.

I am not trying to tell you anything, I got my info off the mozilla page. BTW I tried your command and it works also.

---

