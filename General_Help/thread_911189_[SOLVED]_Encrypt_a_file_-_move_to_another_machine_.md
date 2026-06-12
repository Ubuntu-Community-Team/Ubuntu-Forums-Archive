---
title: "[SOLVED] Encrypt a file - move to another machine and then decrypt"
date: 2008-09-05
forum: General Help
---

### Post by IanB2 on 2008-09-05
I have a couple of files that I'd like to password protect on my main desktop. The problem is that I'd then want to synchronise these files across a couple of laptops and THEN still be able to open the encrypted file on one of my laptops. How would I do this?

I've found a number of articles on how to encrypt and decrypt using seamonkey with e-mail but that is now what I want to do. How can I adapt this method or use something simpler to achieve the above?

---

### Post by Oldsoldier2003 on 2008-09-05
If all the laptops are "yours" you could install gpg on all of them and then encrypt the file using gpg. You would simply need to put your private key on each machine in order to be able to decrypt them. You could use rsynch to keep the files updated with the master copy.

---

### Post by ilrudie on 2008-09-05
I use truecrypt for this.  I have found it to be very reliable.

---

### Post by IanB2 on 2008-09-05
> **ilrudie said:**
> I use truecrypt for this.  I have found it to be very reliable.

I've found a GUI application called easycrypt that uses truecrypt. I've downloaded easycrypt from the repos and the first prompt was to download truecrypt from the truecrypt website. I've done this (although was surprised that truecrypt was not in the ubuntu repos).

I can launch the easycrypt GUI but have been unable to create a new crypt. The GUI just flashes and their are no error messages or dialogues. Any ideas what could be wrong with my installation? (I'm using Mint Elyssa)

---

### Post by ilrudie on 2008-09-05
Don't worry about easycrypt.  Truecrypt has x86 and x64 ubuntu .debs.  I've used both and they both work.

---

### Post by IanB2 on 2008-09-06
> **ilrudie said:**
> Don't worry about easycrypt.  Truecrypt has x86 and x64 ubuntu .debs.  I've used both and they both work.

I'm not red hot on the command line which is why I was hoping to find a simple GUI application to allow me to password protect a file, sync it with one of my other machines and then open it using the same password.

I've tried using the built in encryption methods and cannot decrypt as I cannot figure out how to transfer keys etc to another machine ...... the standard built in tools seem totally baffling and too complex.

Easycrypt was looking good but the GUI on my installation doesn't want to create new crypts!

---

### Post by bingoUV on 2008-09-06
Try mcrypt from repositories. No GUI, but no hassle of keys, just "mcrypt <file name>" to encrypt. It will ask you to enter the password twice.

"mdecrypt <file name>" to decrypt on any other machine, You will need to enter the same password.

---

### Post by ilrudie on 2008-09-06
Truecrypt has a nice gui.  Who said it didn't?

---

### Post by IanB2 on 2008-09-07
> **bingoUV said:**
> Try mcrypt from repositories. No GUI, but no hassle of keys, just "mcrypt <file name>" to encrypt. It will ask you to enter the password twice.

"mdecrypt <file name>" to decrypt on any other machine, You will need to enter the same password.

Just what I was looking for ... thanks.
As I'm sharing a single file across multiple machines, this is perfect. 

The built in encryption methods I'm sure are great for encrypting files on a single PC, but life gets complex if you wish to share across multiple machines (I'm sure on day I'll understand how to set up the 'same' private encryption key on all my boxes).

---

### Post by hyper_ch on 2008-09-07
what do you actually want to do? Whom are you afraid of getting hold of the uncrypted file?

---

### Post by IanB2 on 2008-09-07
> **hyper_ch said:**
> what do you actually want to do? Whom are you afraid of getting hold of the uncrypted file?

I have a couple of old laptops with different distros on them all deb based which I occasionally take out of the house .... the bios is not locked on these machines as I regularly 'play' with them.

I sync my docs folder across all machines and if a laptop went missing, someone with a live CD could read the hard disk (I believe).

I also have an acer aspire one and wish to have the added security of encrypting my 'passwords' file across all machines. Would locking the bios may make it impossible to access the files without the bios password, provided I disable booting from any external media?

---

### Post by hyper_ch on 2008-09-07
still you do not answer the question: Whom or what do you want to protect your files again?

---

### Post by IanB2 on 2008-09-07
> **hyper_ch said:**
> still you do not answer the question: Whom or what do you want to protect your files again?

Theft of sensitive data from laptop if laptop is lost or stolen.

---

### Post by hyper_ch on 2008-09-07
simplest way: full disk encryption

---

### Post by IanB2 on 2008-09-07
> **hyper_ch said:**
> simplest way: full disk encryption

Doesn't this slow down the machine? Bearing in mind that I'm using OLD equipment.

---

### Post by hyper_ch on 2008-09-07
it does - a bit and what do you consider as "old"?

---

### Post by IanB2 on 2008-09-07
> **hyper_ch said:**
> it does - a bit and what do you consider as "old"?

900 mHz pentium III - 256MB RAM.

I know you can encrypt a partition at installation using the alternate install .... but I don't particularly want to re-install the OS. What would you recommend as the best method to encrypt an existing installation? I have one partition '/' for the OS and '/home' (plus SWAP of course)

---

### Post by hyper_ch on 2008-09-07
best open would be reinstall... everything else... is just so much more complicated and time wasting.

you could notice an impact with full disk encryption on those specs...

---

### Post by bingoUV on 2008-09-07
Keep this in mind for your next install, but reinstall for full disk encryption is a big overkill for you. Just encrypt the sensitive directories as you are planning, and you will be fine. Use truecrypt's UI, or mcrypt on command line to encrypt selected directories.

Take care that swap is not used for the machines on which you open the sensitive files. Swap might contain some traces of the files. Also, make sure the software you use for opening the sensitive files does not make a copy in its own area (e.g. /tmp, or ~/.cache)

---

### Post by hyper_ch on 2008-09-07
> **bingoUV said:**
> Just encrypt the sensitive directories as you are planning, and you will be fine. Use truecrypt's UI, or mcrypt on command line to encrypt selected directories.

Problem is we have a journaling filesystem and stuff is saved in different places... if you want real security for data theft, you should know exactely where and what to encrypt... I for myself don't want to spend all that time, hence I use full disk-encryption. So I don't have to worry where something goes on my harddisks.

E.g. you also want to encrypt logs?

---

