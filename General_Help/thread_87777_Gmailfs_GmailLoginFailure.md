---
title: "Gmailfs GmailLoginFailure"
date: 2005-11-08
forum: General Help
---

### Post by makhand on 2005-11-08
I installed gmailfs through synaptic. I'm getting the below error when i try to mount it. 
 ```
gmailfs.py:Gmailfs:unnamed mount options: ['rw']
gmailfs.py:Gmailfs:named mount options: {'username': 'xxxxxxxxxx@gmail.com', 'password': 'xxxxxx', 'fsname': 'blah'}
Traceback (most recent call last):
  File "/usr/share/gmailfs/gmailfs.py", line 1117, in ?
    server = Gmailfs()
  File "/usr/share/gmailfs/gmailfs.py", line 603, in __init__
    self.ga.login()
  File "/usr/lib/python2.4/site-packages/libgmail/__init__.py", line 281, in login
    raise GmailLoginFailure
libgmail.GmailLoginFailure

```
To mount, i used: 
```
 sudo mount -t gmailfs none /home/myusername/Desktop/ -o username=xxxxxxxxxx@gmail.com,password=xxxxxx,fsname=blah 
```
What am i doing wrong?

---

### Post by seraphim on 2005-11-10
nothing ;)

here's a french thread i found, i'll post the important part here.

[http://mirabellug.org/wikini/wakka.php?wiki=InstallationGmailFS](http://mirabellug.org/wikini/wakka.php?wiki=InstallationGmailFS)

(do all the following stuff as root)

download the file
[http://peterhost.dl.sourceforge.net/sourceforge/l/li/libgmail/libgmail-0.1.3.3.tar.gz](http://peterhost.dl.sourceforge.net/sourceforge/l/li/libgmail/libgmail-0.1.3.3.tar.gz)
and extract.

copy the lgconstants.py, libgmail.py and setup.py to /usr/lib/python2.4/site-packages/libgmail/

install the python2.4-dev package via synaptic or apt

cd to /usr/lib/python2.4/site-packages/libgmail/ and type "python setup.py install"

then rename the twiggy:/usr/lib/python2.4/site-packages/libgmail/libgmail.py to __init__.py and the /usr/lib/python2.4/site-packages/libgmail/libgmail.pyc to  __init__.pyc

done.
for me, everything is working fine :)

---

### Post by KingArthur10 on 2006-01-05
I'm having problems myself with this.  I'm getting an error, and as I'm still a linux noob, here it is for someone to maybe help me:

> arthur@MSHOME:~$ sudo mount -t gmailfs none /home/arthur/Desktop/gmail/ -o username=XXXXX@gmail.com,password=XXXX,fsname=blah
arthur@MSHOME:~$ gmailfs.py:Gmailfs:mountpoint: '/home/arthur/Desktop/gmail/'
gmailfs.py:Gmailfs:unnamed mount options: ['rw']
gmailfs.py:Gmailfs:named mount options: {'username': 'XXXXXXX@gmail.com', 'password': 'XXXXXXX', 'fsname': 'blah'}
No messages found
HTTP Error 404: Not Found
Traceback (most recent call last):
  File "/usr/share/gmailfs/gmailfs.py", line 201, in _sendMessage
    if ga.sendMessage(gmsg):
  File "/usr/lib/python2.4/site-packages/libgmail/libgmail.py", line 594, in sendMessage
    items = self._parsePage(req)
  File "/usr/lib/python2.4/site-packages/libgmail/libgmail.py", line 352, in _parsePage
    items = _parsePage(self._retrievePage(urlOrRequest))
  File "/usr/lib/python2.4/site-packages/libgmail/libgmail.py", line 92, in _parsePage
    lines = pageContent.splitlines()
AttributeError: 'NoneType' object has no attribute 'splitlines'
HTTP Error 404: Not Found
Traceback (most recent call last):
  File "/usr/share/gmailfs/gmailfs.py", line 201, in _sendMessage
    if ga.sendMessage(gmsg):
  File "/usr/lib/python2.4/site-packages/libgmail/libgmail.py", line 594, in sendMessage
    items = self._parsePage(req)
  File "/usr/lib/python2.4/site-packages/libgmail/libgmail.py", line 352, in _parsePage
    items = _parsePage(self._retrievePage(urlOrRequest))
  File "/usr/lib/python2.4/site-packages/libgmail/libgmail.py", line 92, in _parsePage
    lines = pageContent.splitlines()
AttributeError: 'NoneType' object has no attribute 'splitlines'
Traceback (most recent call last):
  File "/usr/share/gmailfs/gmailfs.py", line 249, in __init__
    matchInode = m.group(2)
AttributeError: 'NoneType' object has no attribute 'group'


The link provided above did not work for me, so I found the libgmail on sourceforge and used that.  I followed the steps provided exactly, but alas, it was to no avail.  Thanks for any help anyone can give.

---

### Post by jrib on 2006-01-05
```
 sudo mount -t gmailfs none /home/myusername/Desktop/ -o username=xxxxxxxxxx@gmail.com,password=xxxxxx,fsname=blah 
```

For normal mounting, I've used: 
```
 sudo mount -t gmailfs -o username=xxxxxxxxxx@gmail.com,password=xxxxxx,fsname=blah none /home/myusername/Desktop/  
```

and

```
 sudo mount none /home/myusername/Desktop/ -t gmailfs -o username=xxxxxxxxxx@gmail.com,password=xxxxxx,fsname=blah 
```

but never the format you had.  Can you try either of those?

---

### Post by ubuntumaneh on 2006-01-27
"download the file
[http://peterhost.dl.sourceforge.net/...0.1.3.3.tar.gz](http://peterhost.dl.sourceforge.net/...0.1.3.3.tar.gz)
and extract."

Im not being able to open this link. If it is a temporary failure, it is taken more than one day. So if someone could mirror this package or post here (i believe it is very small program) . I would be very helpful.

Thanks

libgmail-0.1.3.3.tar.gz

---

### Post by makhand on 2006-01-27
For all of you that still want to do this, one option is to consider the GSpace extension for firefox. It works pretty well and does what this thing would do. Except its more like an ftp client in appearence.

---

### Post by ubuntumaneh on 2006-01-27
Thanks for the tip. I will try it. But I still would like to have gmailfs here.

---

### Post by s_spiff on 2006-01-28
Just downloaded GSpace, I think it'll work well enough. besides 2 GB isn't a lot of space :(

---

### Post by ubuntumaneh on 2006-02-04
Ok. Let's try it.
Yesterday, february, 3rd, it was realesed a new libgmail at sourceforge:  	libgmail-0.1.4.tar.gz
Here is the site (this link is working up to now):

[http://sourceforge.net/project/showfiles.php?group_id=113492](http://sourceforge.net/project/showfiles.php?group_id=113492)

Download the package and do what was suggested by seraphim.

Good Luck

---

### Post by kupokomapa on 2006-02-05
after following the instractuons and using libgmail 1.4 

sudo ls -lh
ls: gmail: Input/output error
total 4.0K
lrwxrwxrwx  1 root root    6 2006-01-15 13:32 cdrom -> cdrom0
drwxr-xr-x  2 root root 4.0K 2006-01-15 13:32 cdrom0

gmail is the mount point

:cry:

---

### Post by sunny_nwho on 2006-02-05
Gspace is awesome...i can now use my gmail account as a drive....I have some invites left if anyone need gmail account u can mail me at [email]sksunny@gmail.com[/email]...i will be happy to send an invitation..

---

