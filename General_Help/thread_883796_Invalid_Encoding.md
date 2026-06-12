---
title: "Invalid Encoding"
date: 2008-08-08
forum: General Help
---

### Post by change_mode on 2008-08-08
I backed up all my windows files on an openSUSE FTP server before I installed Ubuntu.
Some of these files include special characters and they are displayed correctly in openSUSE.

When I use gFTP to get them to Ubuntu, gFTP displays them as '? (Invalid Encoding)' and after the transfer they still show up wrong.
When I create new files with special characters, there's no problem though.

So I have two questions:

1) Why does the file transfer mess up the names?
2) How can I find all the files with errors to rename them? Searching for '?' (the character substituted for special chars) or 'invalid encoding' (which is attached to all these files) doesn't give any results.

---

### Post by martinolsson84 on 2008-08-10
[http://www.ubuntulinux.se/node/709#comment](http://www.ubuntulinux.se/node/709#comment)

See "Invalid Encoding, comment 1" in link above. It did help the problem for me, though the thread is in Swedish. 

A short translation: 
1. Install: utf8-migration-tool , (use synaptic)
2. Run the guide, and problem should be solved. 

Good Luck, please ask if you need me to clarify. 

/ Martin

---

### Post by Farinetes on 2010-10-05
Lots of thank's, Martin, that worked perfectly and sloved all my invalid encoding files, thanksss!

# sudo aptitude install utf8-migration-tool

;)

---

