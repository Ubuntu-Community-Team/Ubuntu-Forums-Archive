---
title: "Kontact and Thunderbird"
date: 2005-11-17
forum: General Help
---

### Post by Philz on 2005-11-17
Hi, I have now used Kontact for a little while, but would like to change to Thunderbird, is it possible to export the data from Thunderbird to Kontact?

---

### Post by Philz on 2005-11-18
Can no one help me? :(

---

### Post by randcoop on 2005-11-18
Your question is confusing: in the first sentence, it seems you want to move from Kmail to Thunderbird; in the second sentence, it seems you wan to move fom Thunderbird to Kmail.

If you want to go from Kmail to Thunderbird, then it's simply a matter of importing.  In Thunderbird, there is an import option that permits you to browse to the mail file you want to bring in.  Find the Kmail files you want and then import them.

To go the other way, you need to have installed kmail-cvt.  If you have, then Kmail's import function is in th Tools menu.

---

### Post by Philz on 2005-11-20
I am sorry if my question was confusing. I want to go, as you said, from Kontact to Thunderbird, but how do I export my emails from Kontact? I am used to outlook, and the way to export the emails?

---

### Post by asimon on 2005-11-20
[QUOTE=Philz]I am sorry if my question was confusing. I want to go, as you said, from Kontact to Thunderbird, but how do I export my emails from Kontact? I am used to outlook, and the way to export the emails?[/QUOTE]
Sadly Kontact/Kmail has no export function for mails and thunderbrid can not import the kmail automatically, thus it's a little bit cumbersome. There are short instructions in the [Thunderbird FAQ](http://www.mozilla.org/support/thunderbird/faq#kmail):
Just do:

1. Make a new folder in kmail (i.e. the mail component of kontact) and name it inboxmbox.
2. Use mbox as the mailbox format (default is maildir), with maildir it will not work
3. Copy the posts you want to move from kmail to thunderbird into this inboxmbox folder
4. copy or move the "inboxmbox" file to the subfolder "Mail/Local Folders" in your profile folder of thunderbird, i.e. copy "inboxmbox" to "~/.thunderbird/xxxxxxxx.default/Mail/Local Folders/" (the xxxxxxxx part looks different for each thunderbird user, have a look in ~/.thunderbird so see what it's called on your system.
5. Restart thunderbird, it should detect the new folder with the imported mail automatically

I am not sure where kmail saves it's mail, i.e. where you find the inboxmbox file. I think it should be somewhere under ~/.kde/share/apps/kmail/

---

### Post by Philz on 2005-11-20
Thanks a lot, I will try it out :)

---

