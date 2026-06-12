---
title: "Sources list Ignored"
date: 2008-08-22
forum: General Help
---

### Post by VMC on 2008-08-22
I haven't several Ign outputs when I execute the command:

```
sudo apt-get update
```

Output:
> Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-proposed/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-proposed/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-proposed/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-proposed/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Translation-en_US
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Translation-en_US


How do I go about reading the indiviual lines in "/etc/apt/sources.lst"?
Some of the above lines do exists but are ignored for whatever reason. Is there a break down somewhere that explains in detail? If I take , for example "http://us.archive.ubuntu.com hardy-backports", that site does exists, but how about the rest of the line. How do I go about making sure it's "wording" is what "apt-get" is looking for. 

These "Ign" lines at one point worked, that's why there in my "sources.lst". I've read "man sources.list". It's not what I'm looking for.

Thanks.

---

### Post by y-lee on 2008-08-22
I am not sure what exactly you are asking but from what I gather from the posts I have read is this.

**Hit** means apt checked the package list the timestamps match and there are no changes
**Ign** means there are no changes in the pdiff index file so don't bother downloading it

Both are normal message and can be safely ignored.

---

### Post by VMC on 2008-08-22
Thanks. That's a great help. 'man apt-get' doesn't show the Ign or Hit replies.
Unfortunately I deleted the 'Ign' lines in sources.lst thinking they were some sort of errors.

The other thing I wanted to know is how each line in sources.lst is parsed. 
For example, if I open up a browser and type:
[http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
of course it will fail. But if I go to, [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates, that works. The trailing part of the line is what I wanted to know how it is formed.

You helped in your response. I guess I should have looked for an error instead.

---

### Post by y-lee on 2008-08-22
> Thanks. That's a great help. 'man apt-get' doesn't show the Ign or Hit replies.
Unfortunately I deleted the 'Ign' lines in sources.lst thinking they were some sort of errors.

Ok glad that helped and I am hardly an expert but I was thinking the output above terminal output. So if you edited the sources.list file you might want to, and i highly recommend it,  post the file here so we can look at it and see exactly what it now looks like. Btw does **sudo apt-get update** generate any errors when you run it?


> The other thing I wanted to know is how each line in sources.lst is parsed.
For example, if I open up a browser and type:
[http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
of course it will fail. But if I go to, [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates, that works. The trailing part of the line is what I wanted to know how it is formed.

The apt program reads your source.list file the entires are not really meant to be entered into a web browser as far as i know. As to how apt parses this line I am not sure without looking at the code for it, apt-cache, apt-get, apt.conf and so on. Though the man page for sources.list describes the format for a sources.list entry in enough detail for the average user, you may also want to see [URL="https://help.ubuntu.com/community/Repositories/CommandLine"]Repositories Using the Command Line
[/URL]


For more info on apt than most want or need to know i recommend [the debian apt how to manual]("http://www.debian.org/doc/manuals/apt-howto/index.en.html"). I've read this once or twice but am hardly an expert. I use it as reference researching problems people have on the forums if all else fails.

---

