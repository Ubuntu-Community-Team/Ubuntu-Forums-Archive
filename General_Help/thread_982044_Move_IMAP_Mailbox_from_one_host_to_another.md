---
title: "Move IMAP Mailbox from one host to another"
date: 2008-11-14
forum: General Help
---

### Post by CyBuzz on 2008-11-14
I thought I would come to this forum since the web host doesn't have a solution.

I have a web hosting account at bluehost.  I want to move it to lunarpages due to crappy service from bluehost.  What I need to do though is make sure the mailboxes get transferred.  I have 6 accounts that have mail on the server.  Once I make the DNS change, mail.mydomain.com will point to the new host.

I am not an IMAP or mail expert at all.  Does anyone know how I can move the IMAP repository or file or directory for each mail account to the new host?  I am assuming that I will have to move the IMAP repository after the DNS switch has occurred and 'merge' what is in the new one with what is in the old one.

Now I know that I can download all the Mail from the server and then move it to the new server once the switch has occurred.  That would require me to have access to all of the accounts.  I don't and 3 of the 6 account holders are not technical and probably couldn't figure it out.  What I want to happen is when the DNS change occurs, their mail client gets mail from the new server.  The only thing I think they will have to do is set up a new password.

Thanks for any input.

Jeff

---

### Post by lovinglinux on 2008-11-14
I guess the easiest way is using offlineimap.

```
sudo apt-get install offlineimap
```

Then create the following file:

```
gedit ~/.offlineimaprc
```

and add this code to it.

```
[general]
accounts = [COLOR="Red"]**YourAccount**[/COLOR]

ui = Noninteractive.Basic

[Account [COLOR="Red"]**YourAccount**[/COLOR]]
localrepository = [COLOR="Red"]**YourAccount**[/COLOR]LocalMaildirRepository
remoterepository = [COLOR="Red"]**YourAccount**[/COLOR]ServerRepository

[Repository [COLOR="Red"]**YourAccount**[/COLOR]LocalMaildirRepository]
type = Maildir
localfolders = ~/[COLOR="Red"]**Mail/YourAccount**[/COLOR]/

[Repository [COLOR="Red"]**YourAccount**[/COLOR]ServerRepository]
type = IMAP
remotehost = **[COLOR="Blue"]imap.oldserver.com[/COLOR]**
remoteuser = [COLOR="Red"]yourlogin[/COLOR]
remotepass = [COLOR="Red"]**yourpassword**[/COLOR]
ssl = yes

```

I guess you can duplicate each section of the code above for other accounts and change what is in red accordingly. Unfortunately, you need their passwords.

Then run the following command to sync the remote files with local files:

```
offlineimap
```

I guess while you are in the process of migrating the servers you could create a cron job to run offlineimap at least hourly, to keep it in sync.

After changing the DNS, just replace all instances of **remotehost** (in blue color) and run the offlineimap command again. It will sync the local mail folders with the new host

---

### Post by CyBuzz on 2008-11-14
I appreciate your detailed explanation, but I knot know if that is what I am looking for.  I guess I didnt explain well.  I am not hosting this myself and dont have access to offline imap.  

Essentially I need to smoothest transition from bluehost to lunarpages as I can get.

I was hoping that someone here that knew imap would say "Yeah, get directory X from your old host and put it on your server and run Y script to merge it into the new IMAP folder" or somthing of that nature.

---

### Post by lovinglinux on 2008-11-14
> **CyBuzz said:**
> I am not hosting this myself and dont have access to offline imap.

I know. You can install offlineimap on your machine and download/sync the IMAP content from those accounts to your local folder, then sync back to the new host. That is what my explanation does. All you need is to replicate the mail account info on the new server before syncing back, using the same passwords and mail addresses. 

I know this is not the best solution, since you need their account passwords. But this will make sure all mail messages and folders are merged properly.

If you decide to use this method, please do not run the offlineimap command after deleting the mail folders on your machine, otherwise you will delete them on the server as well. Just to be safe, delete ~/.offlineimaprc after completing the migration.

> **CyBuzz said:**
> Essentially I need to smoothest transition from bluehost to lunarpages as I can get.

I was hoping that someone here that knew imap would say "Yeah, get directory X from your old host and put it on your server and run Y script to merge it into the new IMAP folder" or somthing of that nature.

I don't have experience migrating IMAP accounts, but as far as I know, migrating the web site and the mail accounts is just a matter of dumping the entire web site account using the host backup system and restoring it to the new host.

They know how to do it. They probably say they don't know to force you to stay with them. By the way, the server is a Linux machine right? Do you have cpanel access?

No matter what method you use I strongly recommend scheduling the transition in advance and informing the  other users about it, so they can avoid using their accounts during the migrating period and also allowing them to backup their accounts locally.

---

