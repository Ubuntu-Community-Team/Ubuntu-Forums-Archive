---
title: "[SOLVED] ZIP help"
date: 2008-07-26
forum: General Help
---

### Post by DesiDishoom on 2008-07-26
Hey guys, i've tried unzipping the file BFT_Studio.zip from this site [http://freebft.com/](http://freebft.com/) 
but when in the terminal, when i enter "unzip BFT_Studio.zip", i get this error:

Archive:  BFT_Studio.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  BFT_Studio.zip may be a plain executable, not an archive
unzip:  cannot find zipfile directory in one of BFT_Studio.zip or
        BFT_Studio.zip.zip, and cannot find BFT_Studio.zip.ZIP, period.

I get the same error output when trying to open it with Archive Manager. 

Any ideas on how I can extract the files from the archive? Any help would be immensely appreciated!

---

### Post by jamvegan on 2008-07-26
The file command will probably tell you what the file actually is:

```
file BFT_Studio.zip
```

---

### Post by DesiDishoom on 2008-07-26
Thanks for the quick response!

the output of that was:

"BFT_Studio.zip: Zip archive data, at least v2.0 to extract"

I have version 5.52 of unzip...i'm assuming that's the v2.0 it's referring to. unfortunately i don't know where to go from here. I tried running WinRAR through Wine to extract, but it gave me a system beep and froze both times i tried, so i had to Force Quit out of it.

---

### Post by oldos2er on 2008-07-26
Sometimes you see the error "End-of-central-directory not found" when the file is corrupt. Can you try downloading it again? Failing that, try the command "zip -FF BFT_Studio.zip" to try to repair the file.

---

### Post by DesiDishoom on 2008-07-26
haha yep, apparently the download had stopped before completion but hadn't left any remnants of a .part file, so i thought it was complete. 

But you were right, i re-downloaded it and it was about twice as large as the original, and I was able to open/extract it using archive manager! thanks for the help.

---

