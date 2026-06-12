---
title: "How do I open (but not extract) an archive file using the console?"
date: 2008-10-09
forum: General Help
---

### Post by porchrat on 2008-10-09
OK I'm sure this has been answered somewhere before, but I'm having trouble finding the answer (both with searches on ubuntuforums and with google.

Is there anyone out there who can tell how to open (i.e. NOT extract, but merely open) an archive file (.tar, .zip. .rar whatever) from the console.  I'm getting tired of having to use archive manager to look inside them when I don't want to extract them.

I've looked at the "tar" manual and I didn't really see anything in there that could help me, though I would assume you would use the tar command to do this.  It is just that I would like to be able to use other commands like "grep" and "cat" from the console, which obviosuly can't be done from archive manager.

Thanks

---

### Post by az on 2008-10-09
tar tzvf (archive.tar.gz)

But, I use mc (midnight commander) as a console file-manager.  If you open an archive in it, you are shown it's listing.

---

### Post by porchrat on 2008-10-09
when I try that I get this:

```
tar: This does not look like a tar archive
tar: Skipping to next header
gzip: stdin has more than one entry--rest ignored
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

Also I realise I can list them...once I have listed them is it possible to then pipe to a grep commmand?

Something like

```
tar tzvf foo | grep -R "bar" *
```

---

### Post by az on 2008-10-09
What kind of archive is it?

And yes, you can pipe the output as you describe.

---

### Post by porchrat on 2008-10-09
it is a .zip ...which is weird as I thought the "z" argument would route it through gzip...shouldn't gzip handle a .zip?

---

### Post by porchrat on 2008-10-10
bump

---

### Post by wizard10000 on 2008-10-10
> **porchrat said:**
> it is a .zip ...which is weird as I thought the "z" argument would route it through gzip...shouldn't gzip handle a .zip?

gunzip is limited - from the man page -

> Files created by zip can be uncompressed by gzip only if  they  have  a single  member  compressed with the &#8217;deflation&#8217; method. This feature is only intended to help conversion of tar.zip files to the tar.gz format.

To  extract  a zip file with a single member, use a command like gunzip <foo.zip or gunzip -S .zip foo.zip.  To extract zip files with  several members, use unzip instead of gunzip.

unzip -l *filename.zip*

Hope this helps -

---

### Post by porchrat on 2008-10-10
> **wizard10000 said:**
> unzip -l *filename.zip*
Hope this helps -

Worked perfectly...However is it possible to navigate into a .zip archive (or any archive) without actually extracting, like you can do with archive manager GUIs?

---

### Post by geirha on 2008-10-10
> **porchrat said:**
> Worked perfectly...However is it possible to navigate into a .zip archive (or any archive) without actually extracting, like you can do with archive manager GUIs?

As az mentioned, Midnight Commander can do this. Start it with ```
mc
``` select the zip-file with the arrow keys and hit enter.

---

### Post by porchrat on 2008-10-10
> **geirha said:**
> As az mentioned, Midnight Commander can do this. Start it with ```
mc
``` select the zip-file with the arrow keys and hit enter.

I've looked up mc and it seems like a great idea, but is it possible to utilise shell commands while running mc?...Could I grep those directories within that .zip archive while browsing using mc?...doesn't really seem like it.

---

