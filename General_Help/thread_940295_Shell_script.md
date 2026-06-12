---
title: "Shell script"
date: 2008-10-06
forum: General Help
---

### Post by 5tonemgub on 2008-10-06
Hello,
I need help with a a shell script that will scan a selected folder and sub folders for any file with the .doc or .rtf ending and then run the perl script (perl uploader.pl $filenamn.$filetyp).

Thanks.

---

### Post by RequinB4 on 2008-10-06
Most people won't write scripts for you it's far more productive to do it yourself and more educational too :P

You may wish to use something like the following

```

#!/bin/bash
for file in `find -iname *.doc`
perl uploader.pl $file
end

```

The syntax above is probable not correct, but there's the idea.

---

### Post by mikelygee on 2008-10-06
'find' should be able to do it all on its own:

    find . \( -iname \*\.doc -or -iname \*\.rtf \) \
        -exec perl uploader.pl "{}" \;

(Of course, I haven't tested that exact line; no guarantees. I recommend inserting 'echo' after 'exec' before running it to see what commands it will actually try to execute).

If you want a list of the files it found, tack on ' -print' to the end of the command.

'find' is a pretty amazing utility. Definitely worth getting acquainted with.

---

