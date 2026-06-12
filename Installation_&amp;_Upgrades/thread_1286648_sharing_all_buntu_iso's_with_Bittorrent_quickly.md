---
title: "sharing all *buntu iso's with Bittorrent quickly"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by iGadget2 on 2009-10-09
Trying to contribute my little share to the community, I always have my Transmission client running, serving a lot of *buntu iso's to the world.

Now every time a new version is released, I have to:

[LIST=1]
[*]download all the .torrent files
[*]add them to Transmission one by one, specifying the download dir each time.
[/LIST]
Now I'm certain there must be a way to simplify this. I've already found a way to quickly download all the torrent files from releases.ubuntu.com:
```
wget -r -A .torrent http://releases.ubuntu.com/
```Unfortunately, this downloads ALL the torrent files, even the old ones I already have. I haven't found a way yet to just download the .torrent files from a certain release (adding a subpath doesn't seem to work). But that's not a very big issue since moving files isn't that hard or that much work.

So is there any way to automate the entire process? I don't mind moving away from Transmission, if that'll give me more options. In fact, I like to move this process away from my main machine to a still-to-be-installed server which won't be running a GUI anyway.

But for the ordinary user, who would like to contribute but isn't that tech-savy (but does have a broadband connection and a few GB's of diskspace to spare), it would be great to have a simple solution which caches and then shares all (or some) of the *buntu ISO's with the rest of us. Completely legal, simple and (IMHO) incredibly useful.

Would this be 'Blueprint-worthy'? :P

---

### Post by iGadget2 on 2009-10-26
Okay... This post has been here for over two weeks now. No reply whatsoever. What's wrong, don't like the idea? Let me know! Just don't care? Well... just ignore me then :)

Anyway, I've 'discovered' that wget doesn't mind wildcards, so basically if I'd want only the Karmic files of Ubuntu Studio to be downloaded, I could use

[FONT=Courier New]wget -a -R ubuntustudio-9.10*[/FONT] [FONT=Courier New]http://cdimage.ubuntu.com/ubuntustudio/releases/karmic/rc/

[/FONT]The downside is that ALL files are downloaded now, including the ISO's. Anyway, one small step further... now for the rest of it. Have any thoughts / ideas? Please let me know! :P

---

### Post by Mighty_Joe on 2009-10-26
Your idea is great and all, but some of us have been contributing for quite a while by simply seeding the *buntu ISO's we've downloaded for our own use.  Take a look at a [torrent tracker]("http://torrent.ubuntu.com:6969/") and it seems like there's a lot of Ubuntu seeders out there, even without an organized effort.  I guess that's why they call it a "community".

---

