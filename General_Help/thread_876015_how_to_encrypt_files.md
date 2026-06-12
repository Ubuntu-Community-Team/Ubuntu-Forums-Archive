---
title: "how to encrypt files ?"
date: 2008-07-31
forum: General Help
---

### Post by dexter.deepak on 2008-07-31
my seniors had made a project which first encrypted a file and then defragmented it and then saved it to different locations.
though they used some java application for this, i think there must be some linux tool to 
1. defragment a file
2. encrypt it too.
i am actually avoiding java totally , just trying something linux-specific.
just want to show 'em the linux power :guitar:

---

### Post by drs305 on 2008-07-31
gpg is often used in ubuntu. 
```
sudo aptitude install gpgkeys gnupg
```

You can read the "man gpg" page.

Got sidetracked... 
The command would be something like: gpg -e -r "your-key-id" -o newfilename.gpg originalfilename

You can also right click in Nautilus and select 'encrypt'

And tell them linux files don't need defragging!  ;-)

---

### Post by spupy on 2008-07-31
This is a script i use to encrypt/decrypt files. It requires the package called "zenity". Just open a file with it to encrypt it. Open the file with this script again to decrypt it.

```
#!/bin/bash
# Drag&Drop GPG encryption
if [ "$#" -ne 1 ]
then
	zenity --info --title="GiPiGi" --text="Drop file to encrypt/decrypt it."
	exit 1;
#else
	#zenity --info --text="ok"
fi

basename=`basename $1`
ext=`echo $basename | grep -o 'gpg$'`
if [[ $ext != "gpg" ]]
then
	dirname=`dirname $1`
	basename=`basename $1`
	cd $dirname
	zenity --question --title="GiPiGi" --text="Encrypt this file now?\n$1" && (gpg -cq --force-mdc -o $1.gpg --yes $1 || zenity --error --title="Mismatch" --text="The passphrases you entered does not match!")
else
	zenity --question --title="GiPiGi" --text="Decrypt this file now?\n$1" && (gpg -q --force-mdc --yes $1 || zenity --error --title="Mismatch" --text="Wrong password!")
fi
```

---

### Post by dexter.deepak on 2008-07-31
> **drs305 said:**
> 

And tell them linux files don't need defragging!  ;-)

by defragmenting i actually want to split a single file into say 10 parts, and place them in 10 different locations, so that even if a person gets 1 part, he needs yet 9 other parts of the file.

---

### Post by drs305 on 2008-07-31
Here is a really simplistic solution which works.
Encrypted file: test.gpg  (1.7 KB)

To split into 1000 B sections:
```

split --bytes=1000 test.gpg

```

This will split it into 2 parts:
xaa - 1  KB
xab - .7 KB

To join:
```

cat xaa xab >test.gpg

```

Of course, this is a very small file. Adjust the parameters accordingly.

---

### Post by geirha on 2008-07-31
An example using stat and bash arithmetics to divide it into 10 files using split:
```
$ cowsay -f dragon 'Here be dragons' | gpg --encrypt --armor --recipient=$USER >encrypted-file.asc
$ size=$(stat --format=%s encrypted-file.asc)   # gets the size in bytes
$ split --numeric-suffixes --bytes=$((size/10)) encrypted-file.asc encrypted-file.asc.
$ ls -l encrypted-file.asc*
-rw-r--r-- 1 geirha geirha 1330 2008-07-31 21:03 encrypted-file.asc
-rw-r--r-- 1 geirha geirha  133 2008-07-31 21:08 encrypted-file.asc.00
-rw-r--r-- 1 geirha geirha  133 2008-07-31 21:08 encrypted-file.asc.01
-rw-r--r-- 1 geirha geirha  133 2008-07-31 21:08 encrypted-file.asc.02
-rw-r--r-- 1 geirha geirha  133 2008-07-31 21:08 encrypted-file.asc.03
-rw-r--r-- 1 geirha geirha  133 2008-07-31 21:08 encrypted-file.asc.04
-rw-r--r-- 1 geirha geirha  133 2008-07-31 21:08 encrypted-file.asc.05
-rw-r--r-- 1 geirha geirha  133 2008-07-31 21:08 encrypted-file.asc.06
-rw-r--r-- 1 geirha geirha  133 2008-07-31 21:08 encrypted-file.asc.07
-rw-r--r-- 1 geirha geirha  133 2008-07-31 21:08 encrypted-file.asc.08
-rw-r--r-- 1 geirha geirha  133 2008-07-31 21:08 encrypted-file.asc.09

```

And to decrypt:
```
$ cat encrypted-file.asc.* | gpg

You need a passphrase to unlock the secret key for
....

 _________________
< Here be dragons >
 -----------------
      \                    / \  //\
       \    |\___/|      /   \//  \\
            /0  0  \__  /    //  | \ \    
           /     /  \/_/    //   |  \  \  
           @_^_@'/   \/_   //    |   \   \ 
           //_^_/     \/_ //     |    \    \
        ( //) |        \///      |     \     \
      ( / /) _|_ /   )  //       |      \     _\
    ( // /) '/,_ _ _/  ( ; -.    |    _ _\.-~        .-~~~^-.
  (( / / )) ,-{        _      `-.|.-~-.           .~         `.
 (( // / ))  '/\      /                 ~-. _ .-~      .-~^-.  \
 (( /// ))      `.   {            }                   /      \  \
  (( / ))     .----~-.\        \-'                 .~         \  `. \^-.
             ///.----..>        \             _ -~             `.  ^-`  ^-_
               ///-._ _ _ _ _ _ _}^ - - - - ~                     ~-- ,.-~
                                                                  /.-~

```
:D

---

### Post by dexter.deepak on 2008-07-31
> **geirha said:**
> 
```
$ cowsay -f dragon 'Here be dragons' | gpg --encrypt --armor --recipient=$USER >encrypted-file.asc
$ size=$(stat --format=%s encrypted-file.asc)   # gets the size in bytes
$ split --numeric-suffixes --bytes=$((size/10)) encrypted-file.asc encrypted-file.asc.
$ ls -l encrypted-file.asc*
-rw-r--r-- 1 geirha geirha 1330 2008-07-31 21:03 encrypted-file.asc
-rw-r--r-- 1 geirha geirha  133 2008-07-31 21:08 encrypted-file.asc.00
-rw-r--r-- 1 geirha geirha  133 2008-07-31 21:08 encrypted-file.asc.01
-rw-r--r-- 1 geirha geirha  133 2008-07-31 21:08 encrypted-file.asc.02
-rw-r--r-- 1 geirha geirha  133 2008-07-31 21:08 encrypted-file.asc.03
-rw-r--r-- 1 geirha geirha  133 2008-07-31 21:08 encrypted-file.asc.04
-rw-r--r-- 1 geirha geirha  133 2008-07-31 21:08 encrypted-file.asc.05
-rw-r--r-- 1 geirha geirha  133 2008-07-31 21:08 encrypted-file.asc.06
-rw-r--r-- 1 geirha geirha  133 2008-07-31 21:08 encrypted-file.asc.07
-rw-r--r-- 1 geirha geirha  133 2008-07-31 21:08 encrypted-file.asc.08
-rw-r--r-- 1 geirha geirha  133 2008-07-31 21:08 encrypted-file.asc.09

```

And to decrypt:
```
$ cat encrypted-file.asc.* | gpg

```
:D

thanks a lot to all of you...i have every reason to make 'em jealous :guitar:
but geirha ... your method went totally off my head, can you enlighten me over whats going on here ??

there are few queries for all of you. since you all are using gpg, and i rarely know bout how it works.
1. suppose i encrypt and split a file on my linux system, can i get the original file on my friends' linux system ?? 

2. suppose someone accesses the encrypted (not yet split) file from windows (in a dual boot system). will he be able to see my file ?
i suppose on splitting up there should be NO way from windows to get the original file, am i right ?

3. i plan to encrypt and split some of my personal files in my pendrive.
since most of my surroundings are windoze, i may sometime need my encrypted+split files on windows too..does this have a solution ?

---

### Post by geirha on 2008-07-31
gpg is GNU Privacy Guard, GNU's implementation of PGP, Pretty Good Privacy. Now let's say you create a pgp-keypair. You get a public key, and a secret key. The secret key is protected by a passphrase of your choosing, and you and only you should know this phrase. Your friend does the same, and then you trade public keys with each other. You import your friend's key to your list of keys, and he does the same.

If you want to send your friend a private message now, you encrypt it using your friend's public key. The resulting encrypted file can only be decrypted by your friend's secret key. I haven't heard of anyone decrypting a pgp-encrypted file without a secret key, so as long as your friend keeps his secret key secret, he and only he will be able to read your message.

Splitting the resulting pgp-encrypted file is thus rather pointless, it's secure enough as it is. The only reason for spliting it would be if you sent it by e-mail, which usually has a 10-20MiB limit.

Obviously, if you want to keep something for your eyes only, you encrypt it using your own public key, and whoever wants to see it will need the encrypted file, the secret key, and the passphrase. The passphrase can be very long, and contain spaces, so if you make a long sentence, it will take ages for anyone to crack. And if your secret key gets stolen, you have plenty of time to inform your friends that your public key should no longer be used.

I can explain the commands I did above too if you like, but you can do all this from the seahorse utility which is pre-installed in ubuntu. Applications -> Accessories -> Passwords and Encryption Keys.

To encrypt a file or directory, right click it and select encrypt, then choose the key you want to encrypt with from your list of keys. Decrypting is another right-click feature. To export your public key to give it to others, use the passwords and encryption keys utility I mentioned above.

Hope this brings some light on things.

---

