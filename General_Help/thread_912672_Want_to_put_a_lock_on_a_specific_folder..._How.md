---
title: "Want to put a lock on a specific folder... How?"
date: 2008-09-07
forum: General Help
---

### Post by PsychedelicWonders on 2008-09-07
alright I want to lock up a specific folder with a password, how exactly do I go about doing this?

---

### Post by Qloor on 2008-09-07
Try using Crypt Manager.

```
sudo addgroup your-login fuse

sudo apt-get install encfs python2.4-dev python-nautilus subversion

svn checkout http://crypt-manager.googlecode.com/svn/trunk/ crypt-manager

cd crypt-manager

sudo ./install.sh

gcrypt-amanger

```

---

### Post by PsychedelicWonders on 2008-09-07
Hmm, seems I'm stuck here...

Checked out revision 206.
psychedelicwonders@JohnnyScience:~$ cd crypt-manager
psychedelicwonders@JohnnyScience:~/crypt-manager$ sudo ./install.sh
sudo: ./install.sh: command not found
psychedelicwonders@JohnnyScience:~/crypt-manager$ sudo ./install.sh
sudo: ./install.sh: command not found
psychedelicwonders@JohnnyScience:~/crypt-manager$ cd crypt-manager
bash: cd: crypt-manager: No such file or directory
psychedelicwonders@JohnnyScience:~/crypt-manager$ 

what am I doing wrong?

where will the application be then and how will I use it for particular files?

---

### Post by pbotros1234 on 2008-09-07
Do:
```
cd crypt-manager
ls
```

And see what's in there. Or just browse to the folder normally in nautilus.

---

### Post by PsychedelicWonders on 2008-09-07
psychedelicwonders@JohnnyScience:~/crypt-manager$ ls
clean-svn.sh  conceal-gtk  debian          nautilus-conceal  screenshots
conceal       conceal-kde  make-debian.sh  README            TODO
psychedelicwonders@JohnnyScience:~/crypt-manager$ 


what should I do?

---

### Post by Oldsoldier2003 on 2008-09-07
If the file is there it probably isnt executable. try ./sh install.sh instead of mucking about with permissions.

Edit: too slow you already posted. I'm not familiar with the package but make-debian looks promising. have you looked at the website for installation instructions?

---

### Post by PsychedelicWonders on 2008-09-07
No I honestly dont even know what we are trying to do or what I am looking at .  :D

I'm a totally newbie with Ubuntu.

So is this specific password file thing I want not possible?

---

### Post by fballem on 2008-09-07
> **PsychedelicWonders said:**
> No I honestly dont even know what we are trying to do or what I am looking at .  :D

I'm a totally newbie with Ubuntu.

So is this specific password file thing I want not possible?

Would you mind describing _exactly_ what you want to do. For example, and I'm not sure either of these options is right:

[LIST=1]
[*]I want to have one or more files that can only be opened by a specific user or a specific group of users.
[*]I want to be able to set up one or more specific files so that if a user selects a file, they are required to type a password. If they don't know the password, they cannot open the file.
[/LIST]

You may want to provide instructions as to how you think this should work. Once we have that, then the rest of us may be able to provide options that will work.

Thanks,

---

### Post by PsychedelicWonders on 2008-09-07
See here are all of my folders filled with all of my data.

Some of them, I wont mind if someone (friends, girlfriends, etc) happens to be browsing and goes in them.

But the one called "The Website", I want this one to prompt for a password in order to access what is inside of that particular folder.

Is that possible?

Also, I believe that entire crypt package you told me to download is installed... so do I not want to use that one anymore?

---

### Post by hyper_ch on 2008-09-07
everything that is not encrypted can be - with some effort - opened by anyone.

---

### Post by ghostdog74 on 2008-09-07
@OP. You should think up a plan to secure your folder according to who are authorised to access it.

---

### Post by fballem on 2008-09-07
> **ghostdog74 said:**
> @OP. You should think up a plan to secure your folder according to who are authorised to access it.

I would agree with that, but I wanted to make sure that we understood the requirement before we tried to solve the problem.

---

### Post by PsychedelicWonders on 2008-09-07
I'm not worried about hackers.

Just regular friends or girlfriends using my computer like normal.

I dont want them to access a particular file.

once again, is it possible to place a password on particular folders before you are allowed access to them?

---

### Post by PsychedelicWonders on 2008-09-08
So whats the verdict on this?

What about this crypt manager program I downloaded?

Will it allow me to enable a password protection on a particular folder?

---

### Post by hyper_ch on 2008-09-08
if you are ok with that fragments or individual files or parts of them - due to how the system handels files - can be found elsewhere, then you can use one of those cryptotools. TrueCrypt can here be recommended, as it also works good on Mac and Windows. Bascially you want to make a an encrypted file, that you uncrypt and mount on your filesystem and then you can copy files into it.

---

### Post by PsychedelicWonders on 2008-09-15
> **hyper_ch said:**
> if you are ok with that fragments or individual files or parts of them - due to how the system handels files - can be found elsewhere, then you can use one of those cryptotools. TrueCrypt can here be recommended, as it also works good on Mac and Windows. Bascially you want to make a an encrypted file, that you uncrypt and mount on your filesystem and then you can copy files into it.


Hmm.  What do you mean "ok with fragments or individual files or parts of them"?

I would really just like to have it prompt you for a password when you double click on a particular folder.

I'm surprised this isnt easy as cake in this day in age.

---

### Post by hyper_ch on 2008-09-16
it's how journaled filesystems work. There are traces in multiple locations for files... just putting a lock won't protect files completely.

---

### Post by shaggy999 on 2008-09-16
Ok, what you're asking can be done and be done easily. You will need to open up a terminal as you will be using terminal commands.

First you want to change the ownership of the file. My guess is you probably let people use your account to browse the web, so you'll want to change the ownership of the file to root. This is done like this:

chown root:root filename

You then want to change the permissions of the file to something like this: chmod 600 filename

If you're wanting to do this to an entire folder then you need to use 700 instead of 600 when you chmod.

Now in order to work with the files you have to 'gksudo nautilus' then browse to the file and double click it.

This is not the best way to do it, as others have pointed out, but this will keep your friends from accessing the files.

---

### Post by shaggy999 on 2008-09-16
I don't think I was completely clear about the directory thing.

To lock a file: 'chown root:root filename' followed by 'chmod 600 filename'

To lock a directory 'chown root:root directory_name' followed by 'chmod 700 directory_name'

---

