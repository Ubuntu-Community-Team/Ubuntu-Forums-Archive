---
title: "vNote Parser"
date: 2008-10-07
forum: General Help
---

### Post by MusicMastaMike on 2008-10-07
I recently started writing notes on my cell phone and transferring them via bluetooth to my laptop, only to find that they were encoded as vNotes.  I couldn't find any programs to parse through them for me, so here's a little perl script to do it.  Hopefully someone else will find this to be of use.

Extract the script and make it executable with
```
tar xzf vnote.tar.gz
chmod +x vnote.pl
```
and run like this:
```
./vnote.pl <input_file> <output_file>
```

---

