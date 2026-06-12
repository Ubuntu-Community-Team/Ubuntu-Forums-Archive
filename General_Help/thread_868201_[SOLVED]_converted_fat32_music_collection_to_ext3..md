---
title: "[SOLVED] converted fat32 music collection to ext3...now have problems with special ch"
date: 2008-07-23
forum: General Help
---

### Post by evencoil on 2008-07-23
I had a music collection on a fat32 external hard drive which I copied to an ext3 drive. I recently noticed that there were some problems in the copying, mainly that special characters that worked in fat32, like letters with accent marks, were changed to different characters and also that some of the capitalization was messed up.

Now I think that it was probably a bad idea to have filenames with accent marks and special capitalization in the first place, so I'm not concerned about those, but I would like to have a way to automatically go in and clean the filenames. What is a good way to do this? I already started making changes on the ext3 copy that I would like to keep, so recopying is a last resort.

I realize that might not have been so clear, so I'd be pleased to clarify...


EDIT: To clarify, here's an example. I had a directory called
music/collection/Andrés Segovia
which now looks like
music/collection/Andr%E9s%20Segovia

EDIT: figured out a workaround

---

### Post by logos34 on 2008-07-23
you could use EasyTag too:

Alt+P>file settings>replace illegal characters in filename

---

