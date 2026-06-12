---
title: "Find files by Type"
date: 2008-11-03
forum: General Help
---

### Post by Neural oD on 2008-11-03
Hi All 
Hope someone can help!! I've tried googling around - but nothing satisfactory has come up - hence this post. 
What I'm looking at doing is to find all music files on my system and move them to a folder. It would be easy if they all had file extensions like .mp3 or other. The issue is could we use the file command with the find command to make this work? Or is there an easier way? 
BTW - I know how to make xargs work with find, so basically I need to know how to use file with find.

Thanks

---

### Post by geirha on 2008-11-03
One way would be to loop through the list of files find produces, run file on each filename, and do something if it's audio
```
find -type f | while read file; do
  case `file --brief --mime "$file"` in
    audio/*)
      echo "$file is audio"
      echo mv "$file" "/dest/folder"
      ;;
    application/ogg)
      echo "$file is ogg ..."
      ;;
    *)
      echo "$file is not audio"
      ;;
  esac
done

```

Or you can use the -exec option to find
```
find -type f -exec bash -c "file -ib \"{}\" | egrep -q '^audio/|^application/ogg' && echo -en \"{}\0\"" \; | xargs -0 ls
```

For some reason ogg files has mime application/ogg, and not audio/*, even if they only contain audio streams. So you'll have to find a sample of each file type and figure out what pattern or regex to match with. "^audio/" should match most audio files though.

---

### Post by Neural oD on 2008-11-03
Thanks geirha

will give this a try and post any results or questions.

- This community is awsome!!

:guitar:

---

### Post by Neural oD on 2008-11-11
thanks geirha - I have actually recently switched to zsh - so i don't think that the script will work with zsh - but I probably will try to modify it to work with zsh.

---

