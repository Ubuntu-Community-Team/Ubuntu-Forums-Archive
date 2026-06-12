---
title: "Nautilus scripts &quot;copy to&quot; and &quot;move to&quot; not working?"
date: 2008-11-10
forum: General Help
---

### Post by frediE on 2008-11-10
Any script masters out there able to trouble shoot why a script will not work in ubuntu 8.10?   what i would like to do is select a file (or files) in nautilus and copy (or move) them to a folder.  if there is a plugin or something easier then creating a script let me know.

this is where i found the original scripts....
[https://help.ubuntu.com/community/Nautilus_Scripts](https://help.ubuntu.com/community/Nautilus_Scripts)


```

# To copy selected files to a location

LOCATION=$(zenity --file-selection --directory --title="Select a directory") || exit

IFS=$'\n'
for FILENAME in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
do
    if [ -e "$LOCATION"/"$(basename $FILENAME)" ];then
       zenity --question --title="Conflict While Copying" --text="File ""$LOCATION"/"$(basename $FILENAME)"" already exists. Would you like to replace it?"
       case "$?" in
          1  )  exit 1 ;;
          0  )  cp -a -- "$FILENAME" "$LOCATION" ;;
       esac
    else
       cp -a -- "$FILENAME" "$LOCATION"
    fi
done
```



```
# To move selected files to a location

LOCATION=$(zenity --file-selection --directory --title="Select a directory") || exit

IFS=$'\n'
for FILENAME in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
do
    if [ -e "$LOCATION"/"$(basename $FILENAME)" ];then
       zenity --question --title="Conflict While Moving" --text="File ""$LOCATION"/"$(basename $FILENAME)"" already exists. Would you like to replace it?"
       case "$?" in
          1  )  exit 1 ;;
          0  )  mv -f -- "$FILENAME" "$LOCATION" ;;
       esac
    else
       mv -- "$FILENAME" "$LOCATION"
    fi
done
```

---

### Post by frediE on 2008-11-10
i hate it when i answer my own questions.... hopefully it helps the next ubu user.  :-)

make sure you add the following line to the top of the file.  so copy the following code, open the script, and paste it in the top (first line), save and close. 

```
#!/bin/bash
```

---

### Post by giuspen on 2008-11-10
try these scripts:
[http://open.vitaminap.it/en/linux_developments.htm](http://open.vitaminap.it/en/linux_developments.htm)

---

