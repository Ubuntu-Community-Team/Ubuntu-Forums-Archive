---
title: "Gjiten crashes when adding a WordDic file"
date: 2005-11-20
forum: General Help
---

### Post by izm81 on 2005-11-20
At first, it seems to run fine...  But when you try to add a WordDic dictionary file, the program totally freezes.  And without a dictionary file, the program is pretty much useless.  :(  Has anybody gotten this to work, or know what the problem may be?

Thanks.

---

### Post by 4rc on 2005-11-21
I've got the same problem. When I try to add a WordDic file, it says this in terminal and totally freezes:

 *** glibc detected *** free(): invalid pointer: 0xb7cdf580 ***

If I try to set up a KanjiDic it says this:

*** glibc detected *** free(): invalid pointer: 0xb7cb2580 ***

I am a newbie and these error messages don't say a lot to me.. could someone with more experience tell me what is going on and how to possibly make this work? I can reproduce this behavior, if that is of any help.

---

### Post by izm81 on 2005-11-22
Yeah, I get the same message.  It means that it is trying to free memory it's not allowed to free, I believe.  But I thought an error like this would be caused from a (serious) error in the Gjiten code or in the glib library.  Either one, I'm under the impression that it shouldn't be present in Ubuntu.  I don't know if we have done something strange to cause it....

But, I have a workaround:

_Easy, quick way:_ * Don't click "Browse."*  Just type or copy and paste the path to the dictionary files.  Mine were:
[LIST]
[*]/usr/share/gjiten/dics/edict
[*]/usr/share/gjiten/dics/compdic
[*]/usr/share/gjiten/dics/kanjidic
[/LIST]

If that doesn't work, try a _Longer way_ (only here because I wrote it before trying the quick way....)

run **gconf-editor** (type it in a console and press enter).

For _WordDic_ files, use gconf-editor to navigate to **/apps/gjiten/general/** and add paths to your dictionaries to **dictionary_list**.

For _kanjidic_ files (mine was already set up) you can use gconf-editor to navigate to **/apps/gjiten/kanjidic/** and set **kanjidicfile** to be the path to your kanjidic file.

You can then edit the properties for the WordDic files in Gjiten and give them names.  This seems to work.

Hope that helps.

---

### Post by 4rc on 2005-11-23
Thanks a million, the easy way worked fine for me (though you had a small error there - dics, not dicts).

---

