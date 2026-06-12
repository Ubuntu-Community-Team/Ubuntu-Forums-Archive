---
title: "Password protecting applications and folders?"
date: 2008-10-11
forum: General Help
---

### Post by Kinetic Being on 2008-10-11
Is it possible to password protect certain applications and folders, but not have them run as root?

---

### Post by caleb12 on 2008-10-11
Not sure I fully understand what you are asking... what do you mean "but not have them run as root"? 

As far as password protecting... I mean the simplest method to stop other users from being able to read the contents of folders or execute files is setting the UMASK properly... The command:

sudo chown 600 filename.txt

will make a file readable by only the person who created it. 

If you are looking for something more hardcore, like in case the computer is compromised or stolen - look into TrueCyrpt or setting up EncFS.

---

### Post by Kinetic Being on 2008-10-11
I am looking for a way to have it so that whenever tomboy is opened, you need the password to do anything, or even open it up.

I don't want to set tomboy to run as root, which I assumed would make me enter my password.

Not for other accounts, for this one, a password for whenever you open certain programs or folders. I don't need, nor want, it encrypted, just a simple password protection to keep from prying eyes.

---

### Post by caleb12 on 2008-10-11
I see... 

hmmm, don't know of any thing like that off hand... Like I said the only things you can do is to set the umask, which would keep other accounts from being able to look at any of your files. But, something for your account specifically... haven't seen it. 

If you find something, post it... I'd like to know it as well.

---

