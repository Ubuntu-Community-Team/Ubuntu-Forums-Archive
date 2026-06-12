---
title: "how to update the packages index offline"
date: 2008-07-12
forum: General Help
---

### Post by UAA on 2008-07-12
Hello,
running this command will update my software lists
```
sudo apt-get update
```
if I ran this instead
```
sudo apt-get update --print-uris
```
I'll get links to the files that apt-get use to update, OK.

lets say I'm a user without any kind of internet connection and I want to get the latest software list to my Ubuntu system. so I can chose what I want and run "generate download script" from synaptic so I ran this:

```
sudo apt-get update --print-uris | grep ^\' | cut -d\' -f2 > file.txt
```

It gave me the links to the file that the apt-get update gets it's informations from.

in apt-get man page: 
> --print-uris 
....
This also works with the source and update commands. When used with the update command the MD5 and size are not included, and it is up to the user to decompress any compressed files. Configuration Item: APT::Get::Print-URIs.

is that right I mean no other way that if I downloaded these files to do something make the apt-get update command use the files I downloaded instead of the files from the internet.

please provide some way it would be nice to those who doesn't have internet so they can chose the software they want and download it later.

if not (no way) and I have to do it manually by downloading and decompressing the files.
there is a lot of files I don't know what to do with.

[http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)
where should I put it.

the file:
[http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2)
after decompressing it I found a file with the name packages
the files in /var/lib/apt/lists have long names and so I guess I need to change it manually. because  other *.bz2 will contain files with the same name.

those files never get downloaded:
[ftp://***/dists/hardy/main/i18n/Translation*](ftp://***/dists/hardy/main/i18n/Translation*) 

please refer me to a useful article or solution, and off course I prefer an automated way.

I've managed once to download the universe (the biggest) packages list and I had to change its name to the same name as an old list.

---

### Post by UAA on 2010-05-24
[http://keryxproject.org/](http://keryxproject.org/)
is a good solution

---

