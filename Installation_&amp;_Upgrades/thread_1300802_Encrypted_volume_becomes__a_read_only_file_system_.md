---
title: "Encrypted volume becomes  a read only file system after viewing eith EOG"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by markdashabout on 2009-10-25
I have had an encrypted volume on my system for a while. Its encrypted with cryptmount, so that there is a entry in the file

/etc/cryptmount/cmtab 

that looks like this: 

hid3 {
               dev=/home/mark/.hid3 dir=/home/mark/hid3
               fstype=reiserfs fsoptions=defaults cipher=twofish
               keyfile=/etc/cryptmount/hid3.key
               keyhash=md5 keycipher=bf-cbc
               flags=user,nofsck,nomkswap
    }

After upgrade to 9.10 this works as expected, ie to gain access I type 

cryptmount hid3
(passphrase)

and then 

ls hid3

I can also do 

echo a > hid3/a

An Icon appears on my desktop that shows a diskdrive, labelled hid3. If I click on this then I see all the files in hid3 as expected. However, after doing this, the file system has become read only. 

echo a > hid3/a
bash: hid3/a: Read-only file system

Killing the window that now displays the contents of hid3 does not effect a restoration of write permissions. In fact the only thing that does seems to is unmounting and remounting the volume. 

Has anyone come accross anything similar? 

Is this a bug? Has anyone else reported it? 

Can anyone advise a course of investigation?


11th November 09:  Anybody?   I mean how does a file system change to become read only without a change of permissions?

---

### Post by markdashabout on 2010-03-31
Eventually I had no other option than to create a new volume and copy the old data from the new. 

It seemed like there was some data corruption happening in the old volume, so that this was why it became readonly, and probably protected me. 

Alls been good since then.

---

