---
title: "does google earth work proprely in ubuntu?"
date: 2008-08-09
forum: General Help
---

### Post by PsychedelicWonders on 2008-08-09
id like to download google earth... does anyone know how well it works?

is wine needed in order to run it?

---

### Post by zxscooby on 2008-08-09
Yes it works great. Wine is not needed
There is a version in the repositories that can be installed with apt-get and newer versions available for download from the google site. Just unzip and run.

---

### Post by PsychedelicWonders on 2008-08-09
what do I type exactly do download from the repositories?

---

### Post by Seti on 2008-08-09
Personally I prefer to download the binary from google and install that.

[http://earth.google.com/download-earth.html]("http://earth.google.com/download-earth.html")

Download the binary for linux, then make it executable:
```
chmod +x
```

and then run the script:
```
./GoogleEarthLinux.bin
```

cheers

---

### Post by Crafty Kisses on 2008-08-09
> **PsychedelicWonders said:**
> id like to download google earth... does anyone know how well it works?

is wine needed in order to run it?

It works very good for me, I've never had any problems at all.

---

### Post by Vivaldi Gloria on 2008-08-09
> **PsychedelicWonders said:**
> what do I type exactly do download from the repositories?

GE is available in the medibuntu repos:

[http://www.medibuntu.org/](http://www.medibuntu.org/)

Follow the howto there to add medibuntu to your repo list. If you have ubuntu 8.04 hardy heron then these are the commands:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Now you can install GE using synaptic:

system menu > admin > synaptic

---

### Post by PsychedelicWonders on 2008-08-09
> **Seti said:**
> Personally I prefer to download the binary from google and install that.

[http://earth.google.com/download-earth.html]("http://earth.google.com/download-earth.html")

Download the binary for linux, then make it executable:
```
chmod +x
```

and then run the script:
```
./GoogleEarthLinux.bin
```

cheers

How do I make it executable?

Am I just using the terminal like normal?

---

### Post by PsychedelicWonders on 2008-08-09
> **Vivaldi Gloria said:**
> GE is available in the medibuntu repos:

[http://www.medibuntu.org/](http://www.medibuntu.org/)

Follow the howto there to add medibuntu to your repo list. If you have ubuntu 8.04 hardy heron then these are the commands:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Now you can install GE using synaptic:

system menu > admin > synaptic

how is this way better than the one listed above?

---

### Post by Vivaldi Gloria on 2008-08-09
> **PsychedelicWonders said:**
> how is this way better than the one listed above?

In general using repos is better. It's the preferred way of installing programs. Repos contain packages for ubuntu explicitly, synaptic handles dependencies automatically, you get program updates, much easier to uninstall etc. So there are a lot of reasons to prefer using repos and synaptic over installing by hand. I suggest you get used to installing programs using synaptic.

---

### Post by PsychedelicWonders on 2008-08-10
> **Vivaldi Gloria said:**
> GE is available in the medibuntu repos:

[http://www.medibuntu.org/](http://www.medibuntu.org/)

Follow the howto there to add medibuntu to your repo list. If you have ubuntu 8.04 hardy heron then these are the commands:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Now you can install GE using synaptic:

system menu > admin > synaptic

alright youve spoken your case and it makes sense.

So those two codes you gave me, do i enter them separately or together like that?

---

### Post by Vivaldi Gloria on 2008-08-10
> **PsychedelicWonders said:**
> alright youve spoken your case and it makes sense.

So those two codes you gave me, do i enter them separately or together like that?

Copy the first line and paste it in the terminal and press enter. After that do the same with the second line. Then start synaptic. Search & install GE.

Note that those lines are for hardy. You have hardy, right?

---

### Post by StOoZ on 2008-08-10
works perfect for me on Hardy heron (8.04)

---

### Post by PsychedelicWonders on 2008-08-10
yes, 8.04, i will do that now and let you know, thanks.

---

### Post by PsychedelicWonders on 2008-08-10
alright, all is done, now which one(s) do I install?

...

---

### Post by Vivaldi Gloria on 2008-08-10
> **PsychedelicWonders said:**
> alright, all is done, now which one(s) do I install?

...

GE 4.3 and GE 4.3 data.

---

### Post by PsychedelicWonders on 2008-08-10
alright, things seem to be downloading now.

thanks.

so once this is done, where is this program going to be?

all I have to do is drag it to the desktop to get a shortcut correct?

---

### Post by Vivaldi Gloria on 2008-08-10
> thanks.

You're welcome.

> so once this is done, where is this program going to be?

Somewhere in the applications menu. I guess under internet.

> all I have to do is drag it to the desktop to get a shortcut correct?

Yes.

---

