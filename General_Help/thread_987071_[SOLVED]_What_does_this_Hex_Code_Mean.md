---
title: "[SOLVED] What does this Hex Code Mean?"
date: 2008-11-19
forum: General Help
---

### Post by Yuki_Nagato on 2008-11-19
Attempting to open up a .JPG file, Eye of GNOME spits out at:

"This is not a .JPG file because the Hex code 'Ox76 Ox74' starts this file."

That hex code translates into "vt"

What kind of file begins with 'Ox76 Ox74' (O as in the letter.)

---

### Post by hyper_ch on 2008-11-19
how big is the file?

---

### Post by Yuki_Nagato on 2008-11-19
"Properties" states that it is 630 bytes.

Every other file is within 600 to 700 bytes.

These files are random files from the internet, not anything in the Linux system.

Just curious as to how Eye of GNOME uses that hex data it is looking for.  Google is little help in the matter.

---

### Post by cmay on 2008-11-19
not that this provides  answers but. i think there is a plugin in the gimp that can save a image as a c source file. i was playing wiht that one night when i wanted to learn how to customize the themes so i tried to save some files with different images like buttons and so on . i found out that the theme customizing is not done by writing c but xml files instead or at least i did appear that way so i gave up. anyway if that plug in is in the gimp you can see how it works /looks like. i remember when i tried to alter the image i saved as a c source and then reload it as a image in gimp the exact error message showed up.  which is why i follow this tread since i would also like to know some more about this subject. 
thanks for posting.

---

### Post by Yuki_Nagato on 2008-11-20
The data seems to be metadata for actual images in another directory.  Not entirely sure of the whole thing, but the programming idea may be the closest thing to it.

---

### Post by happyhamster on 2008-11-20
Perhaps it's a vti_cnf type of file. If you open it up in a hex-editor (ghex for example), it should start with something like vti_encoding.....vti_author....

For a bit more info, see:
[http://www.frontpagewebmaster.com/m-2110/tm.htm#2110](http://www.frontpagewebmaster.com/m-2110/tm.htm#2110)

---

