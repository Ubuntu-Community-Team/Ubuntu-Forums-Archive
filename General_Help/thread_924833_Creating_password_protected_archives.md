---
title: "Creating password protected archives??"
date: 2008-09-20
forum: General Help
---

### Post by MasterNetra on 2008-09-20
I was wondering if and/or how i could create password protected archives in Ubuntu?

---

### Post by MasterNetra on 2008-09-20
NVM figured it out. Using the default archive program "Archive Manger" i was able to make password protected zips by creating a new zip file, add the files into it, setting the password, then saving as whatever i wanted to call the protected zip. (Note: Don't try to save it as it self as it will kill the entire archive and you will have to start over).

---

### Post by p_quarles on 2008-09-20
The encryption built into Zip's password protection scheme is incredibly weak and won't stand up against anyone who actually wants the data. If you're just trying to keep prying non-technical types out of it, it's fine. For anything else, you'll want real encryption.

---

### Post by MasterNetra on 2008-09-20
Like what?

---

### Post by p_quarles on 2008-09-20
> **MasterNetra said:**
> Like what?
Like GnuPG or Truecrypt.

---

### Post by MasterNetra on 2008-09-20
How do i use GnuPG sense i have it by default? Does it have a GUI display to use if not then what about Truecrypt? After all I am not a Command-line junky...

---

### Post by p_quarles on 2008-09-20
GPG has various graphical front-ends -- nearly all Mail applications, for instance, come with built-in tools, and Gnome has the stand-alone Seahorse program for this purpose. 

Truecrypt comes integrated with a GUI. Having not used that, I don't know much about its use.

That said, using GPG from the command line isn't that difficult. After you have set up your public and private keys, you would encrypt the file using a command such as:
```
gpg -r *name_of_recipient* --sign --encrypt *name_of_file*
```
If you are encrypting a file for your own use, you are the recipient, and you would use an identifier on your own key for that field. GPG doesn't archive files for you, so you would have to create the archive using a separate program like zip or tar. 

To decrypt:
```
gpg --output *new_file_name* --decrypt *file_name.gpg*
```
A new, deciphered copy of the encrypted file is created when you do this, hence the need for the output file. 

But, as I said, there are programs such as Seahorse which will take care of much of the more potentially confusing stuff for you.

---

### Post by MasterNetra on 2008-09-20
meep its alread install by default too it seems... I can't find a Seahorse shortcut in the menu would it be the Passwords and Encryption keys in Accessories?

---

