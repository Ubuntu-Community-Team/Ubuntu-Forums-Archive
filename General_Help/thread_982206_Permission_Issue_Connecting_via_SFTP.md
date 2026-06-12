---
title: "Permission Issue Connecting via SFTP"
date: 2008-11-14
forum: General Help
---

### Post by CarlosinFL on 2008-11-14
I have a Linux file server on the LAN that I connect to when I am logged into my 8.10 Gnome session. I select "Places > Connect To Server" and from there I can see the directory fine but everything is 'Read Only' :confused:

I know I have permissions to that directory and everything else. If I ssh into the directory via CLI, I can rwx as myself. This only happens via the GUI and my co-worker has the exact same problem using Mint Linux (based from Ubuntu) so I am wondering if this is a bug or am I doing something wrong?

Here are my permissions on the file server in question to show you I don't think the file server is to blame unless I am missing something...

```
[carlwill@fback /]$ id carlwill
uid=501(carlwill) gid=501(it) groups=501(it),10(wheel)

[carlwill@fback /]$ ls -l
total 152
drwxr-xr-x   2 root root  4096 Nov  5 04:02 bin
drwxr-xr-x   3 root root  4096 Sep 30 09:10 boot
drwxr-xr-x  11 root root  3960 Oct 31 09:37 dev
drwxr-xr-x  48 root root  4096 Nov 13 13:15 etc
drwxr-xr-x   5 root root  4096 Sep 18 07:04 home
**[COLOR="Red"]drwsrws---   8 root it    4096 Nov 14 12:06 i[/COLOR]**t

```

I attached how I am connecting from Ubuntu and also what I see when I do connect:

It appears the only folder I can write to is the one that my user account owns...

```
[carlwill@fback it]$ ls -l
total 24
drwsrws--- 4 root      it 4096 Oct  7 10:24 carlos
drwsrws--- 9 root      it 4096 Nov 13 13:17 jason
drwsrws--- 6 root      it 4096 Nov 12 10:25 mike
drwsrws--- 2 root      it 4096 Nov 13 12:42 movies
drwsrws--- 3 root      it 4096 Jun 12 12:01 symantec_10.1.7
drwxrws--- 2 carlwill  it 4096 Nov 14 12:06 ubuntu
```

I would think that since I am a member of the 'it' group, then I should be able to rwx to it as well...

---

