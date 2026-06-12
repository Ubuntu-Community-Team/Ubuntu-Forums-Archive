---
title: "do-release-upgrade from 9.04 to 9.10 fails"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by moted on 2009-09-24
I recently tried to upgrade from 9.04 to 9.10a6 and received this error after all packages had been downloaded

> Done [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main evolution-indicator 0.2.4-0ubuntu2
Done downloading            

Upgrading
 * Starting automatic crash report generation: apport                    [ OK ] 


A fatal error occurred 

Please report this as a bug and include the files 
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in 
your report. The upgrade is now aborted. 
Your original sources.list was saved in 
/etc/apt/sources.list.distUpgrade. 

Traceback (most recent call last): 

File "/tmp/tmpyov8iS/karmic", line 7, in <module> 
sys.exit(main()) 

File "/tmp/tmpyov8iS/DistUpgradeMain.py", line 132, in main 
if app.run(): 

File "/tmp/tmpyov8iS/DistUpgradeController.py", line 1593, in run 
return self.fullUpgrade() 

File "/tmp/tmpyov8iS/DistUpgradeController.py", line 1567, in 
fullUpgrade 
if not self.doDistUpgrade(): 

File "/tmp/tmpyov8iS/DistUpgradeController.py", line 997, in 
doDistUpgrade 
self.quirks.run("StartUpgrade") 

File "/tmp/tmpyov8iS/DistUpgradeQuirks.py", line 92, in run 
func() 

File "/tmp/tmpyov8iS/DistUpgradeQuirks.py", line 472, in StartUpgrade 
self._killKBluetooth() 

AttributeError: 'DistUpgradeQuirks' object has no attribute 
'_killKBluetooth' 

Here is a snippet from the /var/log/dist-upgrade/main.log

> 2009-09-24 18:49:41,270 DEBUG cache aufs_rw_dir: /tmp/
2009-09-24 18:49:41,270 DEBUG Free space on /: 377626116096
2009-09-24 18:49:41,270 DEBUG Dir /usr mounted on /
2009-09-24 18:49:41,270 DEBUG Dir /var mounted on /
2009-09-24 18:49:41,270 DEBUG Dir /boot mounted on /
2009-09-24 18:49:41,271 DEBUG Dir /var/cache/apt/archives mounted on /
2009-09-24 18:49:41,271 DEBUG Dir /tmp mounted on /
2009-09-24 18:49:41,271 DEBUG Dir /home mounted on /
2009-09-24 18:49:41,271 DEBUG fs_free contains: '{'/var': <DistUpgradeCache.FreeSpace object at 0x2b25f90>, '/tmp': <DistUpgradeCache.FreeSpace object at 0x2b25f90>, '/usr': <DistUpgradeCache.FreeSpace object at 0x2b25f90>, '/boot': <DistUpgradeCache.FreeSpace object at 0x2b25f90>, '/home': <DistUpgradeCache.FreeSpace object at 0x2b25f90>, '/': <DistUpgradeCache.FreeSpace object at 0x2b25f90>, '/var/cache/apt/archives': <DistUpgradeCache.FreeSpace object at 0x2b25f90>}'
2009-09-24 18:49:41,370 DEBUG linux-image-2.6.31-10-generic (new-install) added with 15728640 to boot space
2009-09-24 18:49:42,116 DEBUG dir '/var/cache/apt/archives' needs '1845742.0' of '<DistUpgradeCache.FreeSpace object at 0x2b25f90>' (377626116096.000000)
2009-09-24 18:49:42,117 DEBUG dir '/usr' needs '1044353024.0' of '<DistUpgradeCache.FreeSpace object at 0x2b25f90>' (377624270354.000000)
2009-09-24 18:49:42,118 DEBUG dir '/usr' needs '52428800' of '<DistUpgradeCache.FreeSpace object at 0x2b25f90>' (376579917330.000000)
2009-09-24 18:49:42,118 DEBUG dir '/boot' needs '15728640' of '<DistUpgradeCache.FreeSpace object at 0x2b25f90>' (376527488530.000000)
2009-09-24 18:49:42,118 DEBUG dir '/tmp' needs '5242880' of '<DistUpgradeCache.FreeSpace object at 0x2b25f90>' (376511759890.000000)
2009-09-24 18:49:42,119 DEBUG dir '/' needs '10485760' of '<DistUpgradeCache.FreeSpace object at 0x2b25f90>' (376506517010.000000)
2009-09-24 18:49:42,119 DEBUG dir '/tmp' needs '0.0' of '<DistUpgradeCache.FreeSpace object at 0x2b25f90>' (376496031250.000000)
2009-09-24 18:50:05,158 DEBUG disabling apt cron job (0755)
2009-09-24 18:50:10,962 DEBUG enabling apport
2009-09-24 18:50:11,019 DEBUG plugins for condition 'StartUpgrade' are '[]'
2009-09-24 18:50:11,019 DEBUG plugins for condition 'karmicStartUpgrade' are '[]'
2009-09-24 18:50:11,020 DEBUG plugins for condition 'from_jauntyStartUpgrade' are '[]'
2009-09-24 18:50:11,020 DEBUG quirks: running StartUpgrade
2009-09-24 18:50:11,021 DEBUG check if patch '_usr_sbin_install-docs.3533d3b8e8f08f78c95550a7edcbe316' needs to be applied
2009-09-24 18:50:11,060 DEBUG check if patch '_usr_sbin_install-docs.268d21f1f1ed5f7a19fffef645ac4d52' needs to be applied
2009-09-24 18:50:11,061 DEBUG skipping 'README' (no '.')
2009-09-24 18:50:11,113 DEBUG killing kblueplugd kbluetooth
2009-09-24 18:50:11,162 ERROR not handled exception:
Traceback (most recent call last):

  File "/tmp/tmpyov8iS/karmic", line 7, in <module>
    sys.exit(main())

  File "/tmp/tmpyov8iS/DistUpgradeMain.py", line 132, in main
    if app.run():

  File "/tmp/tmpyov8iS/DistUpgradeController.py", line 1593, in run
    return self.fullUpgrade()

  File "/tmp/tmpyov8iS/DistUpgradeController.py", line 1567, in fullUpgrade
    if not self.doDistUpgrade():

  File "/tmp/tmpyov8iS/DistUpgradeController.py", line 997, in doDistUpgrade
    self.quirks.run("StartUpgrade")

  File "/tmp/tmpyov8iS/DistUpgradeQuirks.py", line 92, in run
    func()

  File "/tmp/tmpyov8iS/DistUpgradeQuirks.py", line 472, in StartUpgrade
    self._killKBluetooth()

AttributeError: 'DistUpgradeQuirks' object has no attribute '_killKBluetooth'

2009-09-24 18:50:11,165 DEBUG enabling apt cron job


I cant seem to figure out what to do next.  Any help would be appreciated.

---

### Post by paimon.soror on 2009-09-24
I am actually getting the same exact message!  Much help needed since now all of my package sources are disabled and filled with karmic stuff!

---

### Post by paimon.soror on 2009-09-24
Ok i found a way to get past the error.  Once you click the upgrade button in the update manager, you want to suspend the process right BEFORE the dialog that says "Downloading file x of 2" closes.

The way i did it is i fire up a terminal...
then run "sudo update-manager -d"
then click the update button for 9.10
Agree to the terms, and quickly click back to your terminal
once you see the download box pop up, quickly press CTRL-Z

leave the manager suspended and open /tmp/ and sort by date
you should see a folder called tmpXXXXXXX near the top
navigate into that folder and open up the DistUpgradeQuirks.py file
navigate to line 472, and remove the line (should say self._killKBluetooth())

Your file should now look like this

# run right before the first packages get installed
    def StartUpgrade(self):
        self._applyPatches()
        self._removeOldApportCrashes()
        self._removeBadMaintainerScripts()
        self._killUpdateNotifier()
    def jauntyStartUpgrade(self):
        self._createPycentralPkgRemove()
        # hal/NM triggers problem, if the old (intrepid) hal gets

save
now go back to your terminal and type 'fg 1'
the process will continue and all should be well

hope that isn't too confusing, let me know if you need help

---

### Post by paimon.soror on 2009-09-25
Just a heads up, Ive been running 9.10 since last night with no indications of adverse effects from the modification.

---

