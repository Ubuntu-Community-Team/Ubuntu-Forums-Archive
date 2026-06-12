---
title: "Samba &amp; Ebox Errors!"
date: 2008-10-20
forum: General Help
---

### Post by mewejo on 2008-10-20
This is refference to UBUNTU SERVER...

Deal All,

I installed Ubuntu Server on a high spec desktop convert (x64 bit) in June 2008...

I had two users running on it, josh and mel. Josh is me and Mel is my dad. I remember setting it up, I had to reinstall it several times to get it to play ball (samba) as it just would not work and eventually it worked. God knows why it just did... :confused: 

So eventually it worked and I had Shares called, Web Design, Photography, Public, Apache Webserver and Homes for both of us.

It was all dandy, then I went onto Ebox yesterday to make a new user called Wendy, my mum. I did this and it all went through ok. I then (on a Mac Book Pro OS X) disconnected from the server, (bdigital-server) and then connected with Wendy using the password I set in Ebox.

I tested the home directory on Wendy, by creating a new folder and it showed up then fashed away... then i tried to make another new foler and it did exactly the same... I deleted Wendy through Ebox...

I then tried to make an account manually through smbpasswd with:

```
sudo smbpasswd -a Wendy
```

And it asked for a new SMB password and I entered it... and then re-entered it and then it said, failed to edit entry or something along those lines...

So I have been trying to Uninstall, reinstall Samba and Ebox and it just wont work!:( Then I edited smb.conf file and all of that and no joy!

Finally this morning, I got the Photography share working... (it was the only one I was testing to save typing them all out each time) but only me, Josh, could log on. Mel couldnt. Forget Wendy for the moment...

But it was amazingly slow... It lagged, crashed... this i then tried to log on with Mel on XP Pro and it didnt liek the password and/or username and then I clicked ebox internal backups, it said network error, i then tried Photography again and it chugged and loaded but extremely slow. Slower than Josh on the Mac book Pro OS X.

Can I wipe the entire server... and keep all the data on the second disk... a 1 terrabyte with all the shares on (ULTRA IMPORTANT!!) but Apache and home directories...

I WANT TO KEEP EVERYTHING FILE WISE, INCLUDIND HOME DIRECTORIES, AND ALL THE SHARES... I dont want to delete them.

Any ideas please!

I'm killing myself here :(

Thanks in advance!

Regards,

Josh

Ps, it said it couldnt connect to LDAP Server aswell...

---

