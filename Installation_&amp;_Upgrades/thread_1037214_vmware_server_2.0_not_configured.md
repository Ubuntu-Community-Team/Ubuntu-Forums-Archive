---
title: "vmware server 2.0 not_configured"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by buck2825 on 2009-01-11
I figured that I would place this here since this works for me 


The Story:

while messing with my 8.04.1 desktop that I use as an all purpose server.  I was in the middle of using vmware server 2.0 and starting up a windoze vm session when i pulled the plug from my PC.  I restarted and went back to what I was working on, but was unable to log into the vmware server software.  after some searching I found that vmware, for some reason vmware gets in a loop where during shutdown or startup it places /etc/vmware/not_configured on the hard disk.  when this file is present vmware will not allow you to log in.  here is the fix that I have found and that I am using.  works just fine for me. 


sudo pico /etc/init.d/vmware

about line 656 you will see:
if [ "$exitcode" -gt 0 ]; then
# Set the 'not configured' flag
touch "$vmware_etc_dir"'/not_configured'
chmod 644 "$vmware_etc_dir"'/not_configured'
db_add_file "$vmware_db" "$vmware_etc_dir"'/not_configured' \
"$vmware_etc_dir"'/not_configured'
exit 1
fi


Change it to:
#if [ "$exitcode" -gt 0 ]; then
# Set the 'not configured' flag
#touch "$vmware_etc_dir"'/not_configured'
#chmod 644 "$vmware_etc_dir"'/not_configured'
#db_add_file "$vmware_db" "$vmware_etc_dir"'/not_configured' \
# "$vmware_etc_dir"'/not_configured'
#exit 1
#fi


save file, delete /etc/vmware/not_configured 

this in not my fix i found it here

[http://ubuntuforums.org/archive/index.php/t-288018.html](http://ubuntuforums.org/archive/index.php/t-288018.html)

but it works for me.

---

