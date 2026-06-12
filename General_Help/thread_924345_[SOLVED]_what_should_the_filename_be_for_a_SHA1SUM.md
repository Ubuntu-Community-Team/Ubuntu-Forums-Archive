---
title: "[SOLVED] what should the filename be for a SHA1SUM ???"
date: 2008-09-19
forum: General Help
---

### Post by gregconquest on 2008-09-19
I have this in a file I created from a text copy-and-paste named clonezilla.verify.txt

SHA1SUMS
7c0363402983c4d44e37da7edf79c6bad407b7a0  clonezilla-live-1.2.0-25.iso
(There is a list of others checksums in this same text file...)

So, what do I name the checksum for the file, clonezilla-live-1.2.0-25.iso, when I create it in my text editor? clonezilla-live-1.2.0-25.iso.SHA1? With "7c0363402983c4d44e37da7edf79c6bad407b7a0" as the only text inside the file?

I cannot find how to do this. And every way I've tried so far results in a error message saying there was no SHA1SUM . . .

Please, help.
Thank you.
Greg

---

### Post by rbc on 2008-09-19
I may not be understanding what you're after, but name it whatever you want, and yes, the hash value will be the only data in that file. For my own benefit....you downloaded the clonezilla-live.iso, and were provided that sha1sum hash from the website? And now you want to hash it to make sure the sums match? If so, go to terminal, navigate to the directory that the .iso is in, and type this:
sha1sum clonezilla-live-1.2.0-25.iso > clonezillahash.txt

This will run the sha1, then write the result in a file called clonezillahash.txt (or name it whatever you want) That file will be written to whatever directory you are currently in

---

### Post by gregconquest on 2008-09-19
Thanks, rbc. I tried this:

```
sha1sum [COLOR="Red"]-w[/COLOR] clonezilla-live-1.2.0-25.iso > clonezilla-live-1.2.0-25.iso.sha1sum
```and got:
> sha1sum: the --warn option is meaningful only when verifying checksumsthen...
```
sha1sum [COLOR="Red"]-c[/COLOR] clonezilla-live-1.2.0-25.iso > clonezilla-live-1.2.0-25.iso.sha1sum
```and got:
> sha1sum: clonezilla-live-1.2.0-25.iso: no properly formatted SHA1 checksum lines foundthen...
```
sha1sum clonezilla-live-1.2.0-25.iso > clonezilla-live-1.2.0-25.iso.sha1sum
```and just got an empty command line again:
> greg@DIYubuntu:/mnt/DATA1/_1_bittorrent/UBCD$ 

The man page for sha1sum has nothing about using a pipe ">" in verifying sha1sum's. Where is this documented?

And how do I turn on verbose mode or whatever I need to get sha1sum to tell me the file was verified?

It is strange. The man page does not appear to have the information necessary to use the sha1sum command.

Greg

---

### Post by gregconquest on 2008-09-19
OK. Got it. Here is what I did:

```
sha1sum -c clonezilla-live-1.2.0-25.iso.sha1sum
```
and I got:
> clonezilla-live-1.2.0-25.iso: OK

So, in my case, I named the filename to be checked as the first part of the sha1sum file, "clonezilla-live-1.2.0-25.iso" and "clonezilla-live-1.2.0-25.iso.sha1sum". I don't think that was necessary; it just makes the purpose of the file clear from the filename. The next part *is* critical, though. **Inside clonezilla-live-1.2.0-25.iso.sha1sum is the sha1sum, followed by two spaces, and then the filename of the file to be checked.** In this case, the inside of my sha1sum file looked like this:
> 7c0363402983c4d44e37da7edf79c6bad407b7a0  clonezilla-live-1.2.0-25.iso


And the sha1sum command to check the file is:

```
sha1sum -c *filename.of.the.sha1sum.file*
```

Almost simple. The disconnect here is that **the man file for sha1sum says nothing about how to make or name a sha1sum file**. I figured this out from the feedback here and [the wikipedia entry on sha1sum]("http://en.wikipedia.org/wiki/Sha1sum") and trial-and-error.

Thanks,
Greg

PS keyphrases: how to make a sha1sum file, how do I make a sha1sum file?, how to create a sha1sum file, how do I create a sha1sum file?, how to format a sha1sum file, how do I format a sha1sum file?, how to compose a sha1sum file, how do I compose a sha1sum file?, what to name a sha1sum file, what do I name a sha1sum file?

---

