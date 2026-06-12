---
title: "Bashpodder not running in CRON"
date: 2005-11-03
forum: General Help
---

### Post by mstralka on 2005-11-03
I did a reinstall from Hoary to Breezy and reinstalled my bashpodder script in CRON with crontab -e.  When it runs in cron, it will only download one MP3 file from one URL and then it seemingly quits.  The contents of the script have not changed since it worked in Hoary.  Does anyone know of any changes to the way CRON works in Breezy that would cause this problem?  
Here's the crontab
```

57 5 * * * /home/mstralka/bashpodder/bashpodder2.shell

```

Here is the script
```

#!/bin/bash
# By Linc 10/1/2004
# Find the latest script at http://linc.homeunix.org:8080/scripts/bashpodder
# If you use this and have made improvements or have comments
# drop me an email at linc dot fessenden at gmail dot com
# I'd appreciate it!
#
# This revision by Brian Hefferan 2004/02/06, adding configuration options.
# No warranty. It seems to work for me, I hope it works for you.
# Questions /corrections on the additions by Brian Hefferan can be sent to
# brian at heftone  dot  com

#default values can be set here. Command-line flags override theses.
verbose=1
wget_quiet='-q'  #default is -q
wget_continue=
catchup_all=
first_only=
unix2dos=
usetorrents=
sync_disks=
fetchlist='bp.conf'

function usage
{
  echo "
Usage: $0 [OPTIONS]
Options are:
-v, --verbose          display verbose messages. Also enables wget's continue
                      option.
--catchup_all          write all urls to the log file without downloading the
                      actual podcasts. This is useful if you want to subscribe
                      to some podcasts but don't want to download all the back
                      issues. You can edit the podcast.log file afterwards to
                      delete any url you still wish to download next time
                      bashpodder is run.
--first_only           grab only the first new enclosed file found in each feed.
                      The --catchup_all flag won't work with this option. If
                      you want to download the first file and also permanently
                      ignore the other files, run bashpodder with this option,
                      and then run it again with --catchup_all.
-bt --bittorrent       launch bittorrent for any .torrent files downloaded.
                      Bittorrent must be installed for this to work. The
                      the script and bittorrent process will continue running
                      in the foreground indefinitely. You can use ctr-c to
                      kill it when you want to stop participating in the
                      torrent.
--sync_disks           run the "sync" command twice when finished. This helps
                      makes sure all data is written to disk. Recommended if
                      data is being written directly to a portable player or
                      other removable media.
-u, --url_list         ignore bp.conf, instead use url(s) provided on the
                      command line. The urls should point to rss feeds.
                      If used, this needs to be the last option on the
                      command line. This can be used to quickly download just
                      a favorite podcast, or to take a few new podcasts for a
                      trial spin.
-h, --help             display this help message

"
}

if [ -n "$verbose" ]; then wget_quiet='';wget_continue='-c';fi
if test -f urls.temp;then rm urls.temp;fi

# Make script crontab friendly:
cd $(dirname $0)

while [ "$1" != "" ];do
   case $1 in
             -v|--verbose ) verbose=1
                            wget_continue='-c'
                            wget_quiet=''
                         ;;
            -u|--url_list ) shift
                            while [ "$1" != "" ];do
                               echo "$1" >> urls.temp
                               shift
                            done
                            if test ! -f urls.temp
                               then
                               echo "Error: -u or --url_list option specified, but no urls given on command line. quitting."
                                   exit 1;
                            fi
                            fetchlist ='urls.temp'
                         ;;
            --catchup_all ) catchup_all=1
                         ;;
             --first_only ) first_only=1
                         ;;
             -bt|--bittorrent ) usetorrents=1
                         ;;
             --sync_disks ) sync_disks=1
                         ;;
                -h|--help ) usage
                            exit
                         ;;
   esac
   shift
done

# datadir is the directory you want podcasts saved to:
datadir=$(date +%Y-%m-%d)

# Check for and create datadir if necessary:
if test ! -d $datadir
      then
      mkdir $datadir
fi

if test ! -f bp.conf && test ! -f urls.temp;
then
   echo "Sorry no bp.conf found, and no urls in command line. Run $0 -h for usage."
   exit
fi

# Read the bp.conf file and wget any url not already in the podcast.log file:
while read podcast
      do
      number=`expr index "$podcast" @`
      podcastURL=${podcast:$number}
      seenfirst=
      #if [ -n "$verbose" ]; then echo "fetching rss $podcast...";fi;
      for url in $(wget -q "$podcastURL" -O - | tr '\r' '\n' | tr \' \" | \
                   sed -n 's/.*url *= *"\([^"]*\)".*/\1/p' )
              do
	  if [ -n "$first_only" ] && [ -n "$seenfirst" ]; then break;fi
          echo $url >> temp.log
	  
          if [ -n "$catchup_all" ];
          then
              if [ -n "$verbose" ]; then echo " catching up $url...";fi
          elif   ! grep "$url" podcast.log > /dev/null ;
          then
             if [ -n "$verbose" ]; then echo "  downloading $url...";fi

             wget --tries=2 $wget_continue $wget_quiet -P $datadir "$url"
          fi
          seenfirst=1
      done
done < $fetchlist

if test ! -f temp.log && [ -n "$verbose" ];then echo "nothing to download.";fi

if test -f urls.temp; then rm urls.temp;fi
# Move dynamically created log file to permanent log file:
cat podcast.log >> temp.log
sort temp.log | uniq > podcast.log
rm temp.log
# Use bittorrent to download any files pointed from bittorrent files:
if [ "$usetorrents" ]
then
    if ls $datadir/*.torrent 2> /dev/null
    then
          btlaunchmany $datadir
    fi
fi

#http://linc.homeunix.org:8080/scripts/bashpodder/user_contributed/merijn_vogel/bashpodder.shell
# MV: Bittorrent downloading using the commandline bittorrent client from debian
# some extra explanation:
# The bittorrentclient cannot work outside a tty; even the headless variant cannot.
# Therefore the downloads are started in new screen sessions which start out in a detached
# state. These torrents are running forever; sharing the file. One must manually shutdown the
# btdownloadcurses processes by attaching to the screens and quitting the application.
# Also, take not that the .torrent files are not removed; if you start this script more than once a day,
# you may run into problems as two bittorrents will run for the same file.
# I have not figured out how to automate the killing of these torrents, or how to get them grouped in one screen session.
#pushd $datadir
#count=0
#find . -name '*.torrent' | while read torrent ; do
#	count=$(($count + 1))
#	utter "starting bittorrent download number $count in a new screen session"
#	screen -d -m btdownloadcurses --max_upload_rate 8 "$torrent" &
#done

#if [ $count -gt 0 ] ; then
#	utter "started $count torrents.. postprocessing of resulting files need to be done manually, because I cannot detect #the finishing of those downloads. Re-encoding may happen the next time this script starts."
#fi
#popd




# Create an m3u playlist:
ls -1rc $datadir | grep -v m3u | grep -v torrent > $datadir/podcast${datadir}.m3u
sort $datadir/podcast${datadir}.m3u | uniq > $datadir/podcast${datadir}.m3u
if [ -n "$unix2dos" ];then unix2dos $datadir/podcast${datadir}.m3u;fi;

if [ -n "$sync_disks" ]
then
    if [ -n "$verbose" ]; then echo "running sync..";fi;
    sync
    if [ -n "$verbose" ]; then echo "running sync again..";fi;
    sync
fi

if [ -n "$verbose" ]; then echo "done.";fi;
echo $(date +%Y-%m-%d-%H%M%S) finished

```

---

