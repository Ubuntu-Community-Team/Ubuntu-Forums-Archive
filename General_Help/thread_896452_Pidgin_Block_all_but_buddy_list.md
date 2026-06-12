---
title: "Pidgin: Block all but buddy list"
date: 2008-08-21
forum: General Help
---

### Post by Mud.Knee.Havoc on 2008-08-21
I keep setting my ICQ and MSN accounts in Pidgin to block everything except messages from people in my buddy list.  This is because I keep getting messages from Russian spammers every day.

Unfortunately, the change doesn't stick - it always switches back to "block only the users below" with a block list.

I've looked through the blist.xml and prefs.xml files in my .purple directory, but cannot find the spot where it refers to blocking users.

Any ideas?

---

### Post by Axerthon on 2008-08-21
Edit blist.xml, near the end of the file are **<block>** tags.

---

### Post by Mud.Knee.Havoc on 2008-08-21
> **Axerthon said:**
> Edit blist.xml, near the end of the file are **<block>** tags.

Thank you for the reply.  I see the BLOCK tags, but I do not know what it is expecting to block everybody but those in my buddy list.

For example, I can do it manually by selecting "Tools" -> "Privacy" - and here I have a choice to:
A. Allow all users to contact me
B. Allow the users on my buddy list to contact me
C. Allow only the users below (and there's a list)
D. Block all users
E. Block only the users below

I'd like to have B be the default.

The blist.xml has a numbering scheme of its own from what I can tell.  In the ACCOUNT tag (at the bottom, where the BLOCK tags are), there is a MODE= part.  I believe that MODE=3 means "Allow only the users below", MODE=4 means "Block only the users below", and MODE=5 is "Allow only my buddy list to contact me" but it seems that this reverts back to a default upon either shutting the program down or rebooting.  Either that, or something else strange is going on, since it doesn't seem to stick to MODE=5 / "only buddy list" for long.

---

### Post by khc on 2008-08-22
which protocol is this for

---

### Post by Mud.Knee.Havoc on 2008-08-22
> **khc said:**
> which protocol is this for

ICQ and MSN, although I only get spam over ICQ.

It's a day later, and it still switches back to "Only block the users below" from "Allow only my buddy list".  This doesn't help stop the spam at all. :(

---

### Post by chmac on 2008-09-06
Did you find a solution? Were you able to successfully set the block options by editing a file?

If you can, then it would be possible to hack up a little wrapper script to re-set those settings every time pidgin is launched. Creating a script ~/bin/pidgin with something like this:
```
cp ~/.purple/blist.xml.copy ~/.purple/blist.xml
/usr/bin/pidgin
```

That would copy a file over blist.xml every time pidgin is started. Although, thinking about it, that's probably not the problem. Pidgin probably resets the file itself. Maybe you could block write access to the file, something like `chmod -w ~/.purple/blist.xml`. Although that might produce an error or some other weirdness in pidgin.

I've just discovered this thread trying to block MSN spam. So hopefully this setting will stick for me, or I'll hope to figure out a solution. I'll post back if I do! :)

---

### Post by bernardfrancois on 2008-09-06
Maybe you could make the configuration file in question read-only after editing it, so pidgin can't modify it?

```

chmod a-w blist.xml

```

I just set the privacy settings to block everyone except people on my list, and after relaunching pidgin the settings seemed to stick... (But I didn't try to see what happened after a reboot).

I get spam on msn very frequently these days (mostly something like 'I can't start a webcam conversation, please click on this link...').

---

### Post by chmac on 2008-09-06
> **bernardfrancois said:**
> I just set the privacy settings to block everyone except people on my list, and after relaunching pidgin the settings seemed to stick... (But I didn't try to see what happened after a reboot).

Can you post back after your next reboot and let us know how you got on? :)

---

### Post by thestub on 2008-10-07
I haven't checked with my Ubuntu box yet, but the version of Pidgin (2.4.3) on this Mandriva machine (2008.1) keeps the setting, after a fashion.

Set MSN to "Only Allow Users on My Buddy List" and restart Pidgin, and it resets to "Only Allow Those Below".  The list then contains my buddy list.  Not sure if this will survive a reboot - but it looks good.

Perhaps a newer version of Pidgin is required?  Has anyone check the Pidgin developer docs?

---

### Post by chmac on 2008-10-07
> **thestub said:**
> I haven't checked with my Ubuntu box yet, but the version of Pidgin (2.4.3) on this Mandriva machine (2008.1) keeps the setting, after a fashion.

Set MSN to "Only Allow Users on My Buddy List" and restart Pidgin, and it resets to "Only Allow Those Below".  The list then contains my buddy list.  Not sure if this will survive a reboot - but it looks good.

Perhaps a newer version of Pidgin is required?  Has anyone check the Pidgin developer docs?

I'm getting the same thing. I'm not sure if it automatically adds new buddies to the list though. That would be a bit of a bummer if it doesn't.

---

### Post by halka on 2008-10-08
i don't know whether this is common knowledge or not, but pidgin seems to reset its privacy settings after each and every status change -- i was agonizing over this for weeks too. after disabling automatic status changes, the setting seems to hold fast.

---

### Post by ykphuah on 2008-11-05
Check this out
[https://sourceforge.net/projects/pidgin-bs/](https://sourceforge.net/projects/pidgin-bs/)

---

### Post by bernardfrancois on 2009-04-13
> **chmac said:**
> Can you post back after your next reboot and let us know how you got on? :)

It didn't work, the file is still modified (maybe overwritten). But the option indeed changed to 'Allow only the users below', with all users in my list there.
I didn't have any problems with adding new users any more, and the list didn't reset any more. I don't have a spam problem any more. I'm using pidgin 2.4.1 at the moment.

---

