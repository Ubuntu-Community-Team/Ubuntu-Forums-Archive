---
title: "[SOLVED] unix cut -d on null characters?"
date: 2008-08-26
forum: General Help
---

### Post by unutbu on 2008-08-26
I would like to use a command similar to

```

file -0 * | grep --binary-files=text -i ogg | cut -d \0 -f 1

```

to pick off the filenames of ogg files. The above doesn't work because '\0' is not the null character (apparently). What is the bit of magic I'm missing?

---

### Post by -Zeus- on 2008-08-26
> **unutbu said:**
> I would like to use a command similar to

```

file -0 * | grep --binary-files=text -i ogg | cut -d \0 -f 1

```

to pick off the filenames of ogg files. The above doesn't work because '\0' is not the null character (apparently). What is the bit of magic I'm missing?

you're trying to remove the extension from .ogg files?

---

### Post by unutbu on 2008-08-26
No, I just want to be able to list those files which `file` thinks are ogg. I use the -0 flag since some filenames might include spaces. What a world of grief that causes! :)

---

### Post by LateNiteTV on 2008-08-26
neeeebbermind.

---

### Post by -Zeus- on 2008-08-26
why don't you try something a little easier that doesn't involve the null char?

if you want it to be recursive: ```
sudo find . -name * | while read FILE; do TYPE=`file "$FILE"`; [ "$TYPE" = "ogg" ] && echo "$FILE"; done
```

non-recursive: ```
ls -1 | while read FILE; do TYPE=`file "$FILE"`; [ "$TYPE" = "ogg" ] && echo "$FILE"; done
```

I'm not what "file" returns for .ogg files, but you can fix it so that works.

---

### Post by ghostdog74 on 2008-08-27
> **unutbu said:**
> I would like to use a command similar to

```

file -0 * | grep --binary-files=text -i ogg | cut -d \0 -f 1

```

to pick off the filenames of ogg files. The above doesn't work because '\0' is not the null character (apparently). What is the bit of magic I'm missing?
grep has an option to display just the file name that match your pattern.

---

### Post by unutbu on 2008-08-27
Thanks to everyone for the suggestions.

The following all work:
```

file -0 * | grep --binary-files=text -i ogg | cut -d $'\0' -f 1

find . -print | while read FILE; do TYPE=`file "$FILE"`; [[ $(echo "$TYPE" | grep -i "ogg") ]] && echo "$FILE"; done

ls -1 | while read FILE; do TYPE=`file "$FILE"`;  [[ $(echo "$TYPE" | grep -i "ogg") ]] && echo "$FILE"; done
```

ghostdog74, I haven't figured out how to use "grep -l", however, since grep is receiving lines from stdin, not a file. Is there another way?
```

% file -0 * | grep --binary-files=text -l -i ogg
(standard input)
```

---

### Post by ghostdog74 on 2008-08-27
> **unutbu said:**
> 

ghostdog74, I haven't figured out how to use "grep -l", however, since grep is receiving lines from stdin, not a file. Is there another way?
```

% file -0 * | grep --binary-files=text -l -i ogg
(standard input)
```

i suggest you use awk then.
```

file * | awk -F: '/[oO]gg/{print $1}'

```

---

