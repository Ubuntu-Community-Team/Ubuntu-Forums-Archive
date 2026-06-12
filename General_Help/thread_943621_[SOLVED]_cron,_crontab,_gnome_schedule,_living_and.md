---
title: "[SOLVED] cron, crontab, gnome schedule, living and positivity"
date: 2008-10-10
forum: General Help
---

### Post by directcharitycontribution on 2008-10-10
[ R E A L L Y __S O L V E D ]

                  - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
                  - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

[ U P D A T E  --  R E A L L Y  S O L V E D ]

                  - - - - - - - - - - - - - - - - - - - - - - - - - - - - -


[http://ubuntuforums.org/showthread.php?t=1091754]("http://ubuntuforums.org/showthread.php?t=1091754") describes configuring display environment variable.

and

[http://ubuntuforums.org/showthread.php?t=625184]("http://ubuntuforums.org/showthread.php?t=625184")

                  - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

                  - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

Yes, something just WORKED! Will do slow step breakdown copy paste to how to! Zzzzzzzzzzzzzzzzzzzzzzzzz!

->> SEE [How to system-wide cron crontab schedule for now]("http://ubuntuforums.org/showthread.php?t=1123807")  <<-

                  - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

[old parts of post]
positive and basic simples observations towards gnome schedule utility. hence prepended as [SOLVED].

_IS WORKING PROGRESS, SOME WRITING CONTRADICT, SO READINGS MUST MAKE THE BEST INSTRUCTION, WHO MAY BE IMPATIENTED, UNTIL FINISHES_.


get a good overview with 
[LIST][jenniferlinca.wordpress.com/2008/06/10/crontab/]("http://jenniferlinca.wordpress.com/2008/06/10/crontab/")[/LIST]
[LIST][ibm.com/developerworks/linux/library/l-job-scheduling.html]("http://www.ibm.com/developerworks/linux/library/l-job-scheduling.html")[/LIST]  
[LIST][cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/]("http://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/")[/LIST] 
[LIST][linux.com/articles/113656]("http://www.linux.com/articles/113656")[/LIST]

*_SUMMARY_*

The cron sets are some delicates, should probably use alternative 'crontab -u USER -l' for sudo edit command, and when it makes more busy then confusing. This why if we can makes any one should that be happy. So that one is the system-wide crontab one, where he make user entries indicated (the 6th, owner, fields).


[LIST]*_CONFIGURATION AND DIAGNOSTIC COMMANDS AND MESSAGES SEQUENCES_*:

before make changes make folder 'Cron Bucket' for copy files to backup before modding.
use code:[B] history | grep -i cron
[/B] or enable [ubuntuforums - some command logging]("http://ubuntuforums.org/showthread.php?t=250911&highlight=scriptreplay")

'  whereis crontab  -==> locates file
'  whereis cron
'  whereis gnome-schedule
'  ls -la /usr/bin/crontab   -==> determines owner of the file
' system >> admin >> syslog > view > filter > cron  -==> syslog shows cron activities
'  **cat /var/log/syslog | grep -i cron**
'  tail -f /var/log/syslog
' sudo nano -w /etc/cron.allow    -==> administrator make the users who cron system permission
'   **crontab -u USER -l**   -==>  edits all all crontab
'  sudo nano /etc/crontab   -==>  view, (and edit), system/root crontab
'  sudo crontab -u userX -e  -==> edit crontab as userX
'  [http://ubuntuforums.org/showpost.php?p=5268686&postcount=3](http://ubuntuforums.org/showpost.php?p=5268686&postcount=3) crontab test
'  sudo /etc/init.d/cron restart  -==>  forces crontab to recent edits
' [Once the crontab has been created it must be added to the task list by running crontab as shown: # for the logged in user - crontab /path/to/cron/entry # to force a particular user - crontab -u user /path/to/cron/entry]("http://www.zytrax.com/tech/survival/cron.html")

'  copy all desire cronjob entries to 'a tmp holding file' > rm remove existing cronjob files >> system >> admin >> synaptic > re-install cron family apps  > make desire cronjobs in a one crontab, system-wide, file, as administrator AS WELL AS root, not as sudo   ___>>___ apply simplest solution


[LIST][unixgeeks.org/security/newbie/unix/cron-1.html]("http://www.unixgeeks.org/security/newbie/unix/cron-1.html")[/LIST]
[LIST][usenet-forums.com/linux-general/96288-cron-not-working-ubuntu-6-06-a.html]("http://usenet-forums.com/linux-general/96288-cron-not-working-ubuntu-6-06-a.html")[/LIST]


*_DEFAULT AND EXAMPLES CRONTAB SETTINGS_*:


[LIST]**[file:///var/lib/dpkg/info/cron.list]("file:///var/lib/dpkg/info/cron.list")**[/LIST]  -==>  sure make ALL files good

**[LIST]man -s 5 crontab**[/LIST]


CONTENTS OF: /etc/crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user command
17 * * * * root cd / && run-parts --report /etc/cron.hourly
25 6 * * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6 * * 7 root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6 1 * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#
This is the default ubuntu version of "/etc/crontab".


[LIST]
 [playlist Alarm]("http://www.federicopistono.org/Set_up_an_MP3_OGG_Alarm_Clock_Using_Linux")[/LIST]
[LIST][ubuntuforums.org - HowTo make cron run GUI applications]("http://ubuntuforums.org/showthread.php?t=105250")[/LIST][/LIST]


*_WORKING SOLUTION_*: 

use code: sudo gedit /etc/crontab        ----=> to enter tasks, copied from user crontab, to system-wide crontab. The entry format nees to be as shown here, [martin.ankerl.com/2008/01/24/howto-get-enough-sleep-despite-stumbleupon-with-ubuntu/]("http://martin.ankerl.com/2008/01/24/howto-get-enough-sleep-despite-stumbleupon-with-ubuntu/").

[Once the crontab has been created it must be added to the task list by running crontab as shown: # for the logged in user - crontab /path/to/cron/entry # to force a particular user - crontab -u user /path/to/cron/entry]("http://www.zytrax.com/tech/survival/cron.html")

use code: sudo nano -w /etc/cron.allow        ----=> to validate user for user crontab.

remove exist crontabs

re-install cron family apps

 crontab -u USER -e rebuilds his cronjobs comprehensive together file

permission etc/crontab allow /HOMEUSER to edit AS WELL AS them root.


[LIST]*_Observations_*

1. [ubuntuforums.org "gnome-schedule is working again. It got fixed while I was trouble shooting some other problems."]("http://ubuntuforums.org/showthread.php?t=747331")  -- OF INTEREST ONLY: apparently solved problem but cause access and security issues. It does show big problem is permissions.


2. probably likely people doesn't wants atonnesofdrama, people may asking later, so just so they knows AS SOON AS POSSIBLE, what is the ABRACADABRA, huh?

is it?

code: chmod 4755 /usr/bin/crontab
code: sudo edit /etc/crontab
code: sudo nano -w /etc/cron.allow
code: sudo find /var/spool/cron -ls
code: sudo touch /etc/cron.deny

3. gnome-schedule has a 'run task' feature. this means computers user can part test the crontab command elements. 

if the scheduled command works from here on the 'run task' mode, that is plus and that part correct, and hook up functioning problems were elsewhere.

this method also lessens any risk of running u harmful direct command via terminal.

4. gnome-schedule tell u what 'flavor/style' u task is.

5. if computer u want, u can use 'edit mode' toggle switch, in gnomes- schedule, where u can copy to display somewhere raw crontab entry vocabulary, or only appreciate in its GONE GEEKY.

6. gnome-schedule can replace q-launchers even if not syncing with crontab and the whole cron process.

7. but gnome-schedule is better making work when he the crons files set knows better.

_*LINKS:*_

[bugs.launchpad.net/ubuntu/+source/cron/+bugs/all]("https://bugs.launchpad.net/ubuntu/+source/cron/+bugs?search=Search&field.status=New&field.status=Incomplete&field.status=Confirmed&field.status=Triaged&field.status=In+Progress&field.status=Fix+Committed&field.status=Fix+Released&field.status=Invalid&field.status=Won%27t+Fix&field.omit_dupes.used=")
[bugs.launchpad.net/ubuntu/+source/cron/+bug/open]("https://bugs.launchpad.net/ubuntu/+source/cron")
[bugs.launchpad.net/cron+OR+crontab+OR+gnome-schedule]("https://launchpad.net/+search?field.text=cron+OR+crontab+OR+gnome-schedule&field.actions.search=Search")
[ubuntuforums.org - HowTo make cron run GUI applications]("http://ubuntuforums.org/showthread.php?t=105250")

[ubuntuforums.org/tags.php?tag=gnome+schedule]("http://ubuntuforums.org/tags.php?tag=gnome+schedule")

[ubuntuforums.org "Novice: crontab - missing something basic"]("http://ubuntuforums.org/showthread.php?t=847446&highlight=%2Ftmp%2Fcrontab")
[ubuntuforums.org "no crontab for root"]("http://ubuntuforums.org/search.php?searchid=49391494")

[unix.com/answers-frequently-asked-questions/13527-cron-crontab.html]("http://www.unix.com/answers-frequently-asked-questions/13527-cron-crontab.html")
[gnome-schedule.sourceforge.net/]("http://gnome-schedule.sourceforge.net/")
[manpages.ubuntu.com gnome-schedule.html]("http://manpages.ubuntu.com/manpages/intrepid/en/man1/gnome-schedule.html")
[help.ubuntu.com/community/CronHowto]("http://help.ubuntu.com/community/CronHowto")
[martin.ankerl.com/2008/01/24/howto-get-enough-sleep-despite-stumbleupon-with-ubuntu/]("http://martin.ankerl.com/2008/01/24/howto-get-enough-sleep-despite-stumbleupon-with-ubuntu/")
[math-linux.com/spip.php?article45]("http://www.math-linux.com/spip.php?article45")
[ubuntuforums.org  "crontab permissions problems??"]("http://ubuntuforums.org/showthread.php?t=625184")
[http://ubuntuforums.org/showthread.php?t=926226](http://ubuntuforums.org/showthread.php?t=926226)
[http://ubuntuforums.org/archive/index.php/t-572105.html](http://ubuntuforums.org/archive/index.php/t-572105.html)

[websearch "gnome schedule" 'outside']("http://www.google.co.uk/search?num=50&hl=en&q=%22gnome+schedule%22")[/LIST]


*_PROBABLE SOLUTION_*

[LIST][plawrence.com/Unixart/cron.html]("aplawrence.com/Unixart/cron.html")

use code: 

[sudo find /var/spool/cron -ls]("http://ubuntuforums.org/showthread.php?t=625184")

[sudo touch /etc/cron.deny]("http://ubuntuforums.org/showthread.php?t=831843")

chmod 4755 /usr/bin/crontab[/LIST]


*_CONCLUSSION_*:

Don't you come back no more.

---

### Post by Titan8990 on 2008-10-10
I don't understand the question here.

---

### Post by Sycron on 2008-10-10
Neither I.

---

### Post by Titan8990 on 2008-10-10
While reading again it sounds like he is explaining how good his GUI crutch is.

---

### Post by directcharitycontribution on 2009-04-03
[SOLVED] as in post 

[http://ubuntuforums.org/showthread.php?t=1123807](http://ubuntuforums.org/showthread.php?t=1123807)

-------------------------------------------------------------------------------------

See [http://ubuntuforums.org/showthread.php?t=1091754](http://ubuntuforums.org/showthread.php?t=1091754)

and 

[http://ubuntuforums.org/showthread.php?t=625184]("http://ubuntuforums.org/showthread.php?t=625184")



[http://earlruby.org/2008/08/update-pidgin-status-using-cron/](http://earlruby.org/2008/08/update-pidgin-status-using-cron/)

[http://www.uluga.ubuntuforums.org/tags.php?tag=cron+crontab](http://www.uluga.ubuntuforums.org/tags.php?tag=cron+crontab)

[http://www.uluga.ubuntuforums.org/showthread.php?t=1053936](http://www.uluga.ubuntuforums.org/showthread.php?t=1053936)

[http://www.siriusventures.com/why-i-hate-ubuntu-sometimes-crontab-not-enabled/](http://www.siriusventures.com/why-i-hate-ubuntu-sometimes-crontab-not-enabled/)

[http://www.nabble.com/What%27s-wrong-with-cron--td22330138.html](http://www.nabble.com/What%27s-wrong-with-cron--td22330138.html)

---

