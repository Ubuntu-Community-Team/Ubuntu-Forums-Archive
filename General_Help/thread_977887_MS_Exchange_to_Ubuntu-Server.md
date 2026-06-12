---
title: "MS Exchange to Ubuntu-Server"
date: 2008-11-10
forum: General Help
---

### Post by bitphire on 2008-11-10
Hello,

I need to find a way to pull everything off of a MS Exchange server and put it on my Ubuntu-Server.

Will be flying to a client that is running a MS Exchange server and we need to get all of the information off his server onto our server. I have never played with a MS Exchange server so I need all the advice I can get on how to accomplish this. It is only a 2 client MSE Server so I don't think it has a lot of data. To be more specific, my boss will be flying up there and I'll be ssh'd into our server doing what needs to be done. Just looking for some idea's. Thanks!

---

### Post by Titan8990 on 2008-11-10
I would be interested hear responses to this. MS Exchange is fairly proprietary and very tied in to Active Directory. It ignores many RFCs in regards to Email. Also, it does not store it's email in a human readable single file (or multiple file depending on your configuration) like a UNIX based email server would.

---

### Post by bitphire on 2008-11-10
> You can export mailboxes to PST files using exmerge, and then read those using readpst under Linux

Suggested on IRC for the E-Mail. From the sound's of it the server might do more than just E-Mail?

---

### Post by Titan8990 on 2008-11-10
Exchange servers also do things such as Calenders, synchronized address books, and its OWA that uses IIS.

---

### Post by Coreigh on 2008-11-10
To expand on bitphire's post use each user's Outlook client to create a PST archive of their entire mailbox. Don't use archive. Log in as the user open outlook and go to _F_ile >> Ne_w_ >> Personal Folders _F_ile (.pst)...

Choose an easy location to save it like Desktop, the default is buried.
Name it something logical like the users name.
Use No Encryption to make it simple.

The new PST will show up as a folder in the mailbox. In the File Menu choose View and Folder list. Expand the new folder and drag or copy everything relevant from the Outlook Today mailbox in to the users PST. Make sure to chise Copy and not Move. This allows you a fail-safe or fallback position.

When Done right-click the PST folder and choose Close, then exit outlook.

The PST will be where you saved it and you can copy it where you need to.

Personal items will all copy to a PST, mail contacts calendars etc. If there are public folders you should be able to create a PST for those too PROVIDED that the user has access and permissions to open the folders.

Note: This will not copy Exchange settings only users mail and contacts ,etc.

---

### Post by bitphire on 2008-11-11
Thanks Coreigh, I will be sure to pass that on to my boss!

---

