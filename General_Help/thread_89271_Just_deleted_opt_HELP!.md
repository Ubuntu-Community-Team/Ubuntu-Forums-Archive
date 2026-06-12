---
title: "Just deleted /opt HELP!"
date: 2005-11-12
forum: General Help
---

### Post by Haegin on 2005-11-12
Hi, I just managed to delete /opt and I can't get it back. Is there any way I can? I checked ~/.Trahs and /root/.Trash to no avail. Thanks for any help - sorry if this post looks odd - im using elinks as I had the latest version of firefox  installed in opt... :( Thanks again

update - I got the normal (default in repositories) version of firefox back again). Now the only program I don't have which was in opt is skype but I can live without its ugly kde interface. I never really used it anyway (I had a whole 2 contacts...)

---

### Post by Haegin on 2005-11-12
Ok, so I stupidly delete /opt and cant restore it. Then, less than 10 minutes later, I delete my sources.list. At this point I start looking for a way to restore files deleted using rm. The first way I found was altering rm so all deleted files are stored in an archive which can be accessed to restore them. Here is the script: (Note - all this is adapted from Linux Gazette #8)

```
#!/bin/bash

# Configuration

# the real 'rm' command
bin_rm=/bin/rm  

# where archiving the files
Archive=~/.rm_saved.tar
# you may prefer something like :
# Archive=/var/trash/$USER/saved_file.tar
# (with write access permission on the directory)

# global variables for the options
Opt_recursive=0
Opt_no_secure=0
Opt_restore=0
Opt_rm=""

# function for archiving a file or a directory
save_file() {
  if [ $Opt_no_secure -ne 1 ] ; then
    # set date/time of deletion
    touch "$1" > /dev/null 2>&1 
    if [ -f $Archive ] ; then
      tar --delete -f "$Archive" "$1" > /dev/null 2>&1
      tar -rf "$Archive" "$1" > /dev/null 2>&1
    else
      tar -cf "$Archive" "$1" > /dev/null 2>&1
      # r/w access only for the user
      chmod 600 "$Archive"
    fi
  fi
}

# function for restoring file or directory
restore_file () {
  if [ -f $Archive ] ; then
    tar -xf "$Archive" "$1" > /dev/null 2>&1
    tar --delete -f "$Archive" "$1" > /dev/null 2>&1
  fi  
}


# reading the command-line args
while getopts "dfirRvns-:" opt ; do
  case $opt in 
    d )  Opt_rm="$Opt_rm -d" ;;
    f )  Opt_rm="$Opt_rm -f" ;;
    i )  Opt_rm="$Opt_rm -i" ;;
    r | R )  Opt_recursive=1
             Opt_rm="$Opt_rm -r" ;;
    v )  Opt_rm="$Opt_rm -v" ;;
    n )  Opt_no_secure=1 ;;
    s )  Option_restore=1 ;;
    - )  case $OPTARG in
           directory )   Opt_rm="$Opt_rm -d" ;;
           force )       Opt_rm="$Opt_rm -f" ;;
           interactive ) Opt_rm="$Opt_rm -i" ;;
           recursive )   Opt_recursive=1 
                         Opt_rm="$Opt_rm -r" ;;
           help )        $bin_rm --help
             echo "(rm_secure)"
             echo "  -n, --nosecure        delete without backup"
             echo "      --viewtrash       list the saved files"
             echo "      --emptytrash      erase the saved files"
             echo "  -s, --restore         restore the specified files"
                         exit 0 ;;
           version )     $bin_rm --version
                         echo "(rm_secure 1.0)"
                         exit 0 ;;
           verbose )     Opt_rm="$Opt_rm -v" ;;
           viewtrash )   if [ -f $Archive.gz ] ; then
                           tar -tvzf $Archive.gz
                         fi
                         exit 0 ;;
           nosecure )    Opt_no_secure=1 ;;
           emptytrash )  if [ -f $Archive.gz ] ; then
                           $bin_rm $Archive.gz
                         fi
                         exit 0 ;;
           restore )     Opt_restore=1 ;;
           * )           ;;
         esac ;;
    ? )  ;;
  esac
done

shift $(($OPTIND - 1))

gunzip $Archive.gz > /dev/null 2>&1

# restoration ?
if [ $Opt_restore -ne 0 ] ; then
  while [ -n "$1" ] ; do
    restore_file "$1"
    shift
  done
  exit 0
else
  while [ -n "$1" ] ; do
    if [ -d "$1" ] ; then
      # the directories are archived only with
      # the -r option
      if [ $Opt_recursive -ne 0 ] ; then
        save_file "$1"
      fi
      $bin_rm $Opt_rm $1    
    elif [ -e "$1" ] ; then
      # existing file
      save_file "$1"
      $bin_rm $Opt_rm $1
    else
      # let 'rm' give his error message
      $bin_rm $1
    fi
    shift
  done
fi

nice gzip $Archive > /dev/null 2>&1 &

# -- end of script --
```

Save this as "/usr/local/bin/rm_secure" then do the following:

```

$ sudo chmod 755 /usr/local/bin/rm_secure
$ sudo chown <your username> /usr/local/bin/rm_secure
$ alias rm='/usr/local/bin/rm_secure'
$ rm --help

```

After this you can use rm as normal but when you delete something you dont want to delete you can get it back. (Details of how to get it back are in rm --help)

Here is an example:

```

$ ls -l
$ rm --viewtrash$ ls -l
$ ls -l
-rw-r--r--  1 ccb   users    22 May 26 10:35 1996 important_file
-rw-r--r--  1 ccb   users    23 May 26 10:35 1996 not_important
$ rm --restore important_file
$ ls -l
-rw-r--r--  1 ccb   users    22 May 26 10:35 important_file
$ rm --viewtrash
-rw-r--r--  1 ccb   users    23 May 26 10:35 1996 not_important
$ rm --emptytrash
$ rm --viewtrash

```

Hope this helps others avoid my predicament!

---

### Post by crane on 2005-11-12
Did you delete it through the browser or with rm command in terminal? 
You should be able to just sudo mkdir /opt to ad it back to the file system. But if it was deleted using rm command everything is probably gone.

One other note. Did you have /opt on a different partition?

---

### Post by Haegin on 2005-11-13
I deleted it through rm and I didn't have opt on a seperate partition. I've managed to recover now but along the way I found the useful script above...

Thanks for the help

---

