---
title: "rsync failing over ssh"
date: 2008-09-02
forum: General Help
---

### Post by Mr Sprout on 2008-09-02
Howdy all,

I've been following the tutorial at [http://ubuntuforums.org/archive/index.php/t-15082.html](http://ubuntuforums.org/archive/index.php/t-15082.html) in order to set up an automated backup for my laptop on the home network. I'm able to ssh to my laptop with absolutely no trouble, but when using the following command to remotely rsync from it the whole thing falls apart:

```
rsync -e ssh -varuzP /media/vault/Backups/Parakeet/ 192.168.0.11:/Pictures/
```

Here's what's returned to me. 
```

building file list ... 

1 file to consider



sent 76 bytes  received 20 bytes  192.00 bytes/sec

total size is 0  speedup is 0.00

```

The folder contains 50GB worth of family photos, anyone have any idea what's up?

Thank you.

---

### Post by monkeyking on 2008-09-02
I don't get what you are trying to do.

When I look at your command it seems that you want to maintain an up todate folder at 192.168.0.11 from paraket?

But what is all this 
```

rsync -e ssh -varuzP 

```

parameters?

I normally just do 

```

rsync -avz fromdomain.com:/home/folder/ ./

```


I don't understand why you use ssh as an argument. If you don't supply anything,
the default is sshport I think. 


If you rsync this way,
then you can easily set up a cronscript that will keep the end folder up to date.

good luck

---

### Post by Mr Sprout on 2008-09-02
I'm attempting to maintain an up to date folder on my local machine from the computer at ip address 192.168.0.11, the ip is there so it knows where to ssh to. I'm getting all this from the tutorial linked in my original post. 

Perhaps it's inaccurate/outdated?

---

### Post by monkeyking on 2008-09-02
I still don't get it.
the man for rsync says.
```

AME
       rsync - faster, flexible replacement for rcp

SYNOPSIS
       rsync [OPTION]... SRC [SRC]... DEST
       rsync [OPTION]... SRC [SRC]... [USER@]HOST:DEST
       rsync [OPTION]... SRC [SRC]... [USER@]HOST::DEST
       rsync [OPTION]... SRC [SRC]... rsync://[USER@]HOST[:PORT]/DEST
       rsync [OPTION]... SRC
       rsync [OPTION]... [USER@]HOST:SRC [DEST]
       rsync [OPTION]... [USER@]HOST::SRC [DEST]
       rsync [OPTION]... rsync://[USER@]HOST[:PORT]/SRC [DEST]


```

it says SOURCE then destination.

So if all your photos are at ip 192.168.0.11.

Then you should swap the 2 arguments.

I haven't read read your guide,
but it seems strange you type in all these arguments.

For the sake of simplicity lets call the parakat com1 and 192.168.01 for com2

If all the files are at com2, and I want them at com1

Then I would type in from com1
```
rsync -avz com2:/folder ./ 
```
or If I was sitting at com2
```
rsync -avz ./ com1:/folder 
```

But I were you I would make a small directory,
before trying to copy all the files,
just to check if it works so you don't accidently delete them.

---

### Post by Mr Sprout on 2008-09-02
Hrm, these suggestions don't seem to be working.

When I'm using rsync locally I always put the place I want the files copied to before the place I'm copying from and it works fine. Could someone suggest an alternative method for using this over a ssh connection?

---

