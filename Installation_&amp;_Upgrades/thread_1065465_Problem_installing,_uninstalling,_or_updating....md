---
title: "Problem installing, uninstalling, or updating..."
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by Dark Samurai on 2009-02-09
Hey all-
When I go to install, uninstall, autoremove, or update, I get a weird message about PostgreSQL.  For example:
```
dark@Gaia:~$ sudo apt-get autoremove
[sudo] password for dark: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up postgresql-8.3 (8.3.5-0ubuntu8.10) ...
 * Starting PostgreSQL 8.3 database server                                       * Insecure directory in $ENV{PATH} while running with -T switch at /usr/share/postgresql-common/PgCommon.pm line 654.
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.3, action "start" failed.
dpkg: error processing postgresql-8.3 (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 postgresql-8.3
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Help please!

---

### Post by Dark Samurai on 2009-02-16
Bump

---

### Post by tommcd on 2009-02-16
Do you know what happened, or what you may have done, to cause this?

In any case, try these commands from terminal:
```
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```

If this does not work, post the output of those commands.

---

### Post by Dark Samurai on 2009-02-16
I dis not do anything that would cause this; I noticed it first after getting an error message after an update.
```
dark@Gaia:~$ sudo dpkg --configure -a
Setting up postgresql-8.3 (8.3.5-0ubuntu8.10) ...
 * Starting PostgreSQL 8.3 database server                                       * Insecure directory in $ENV{PATH} while running with -T switch at /usr/share/postgresql-common/PgCommon.pm line 654.
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.3, action "start" failed.
dpkg: error processing postgresql-8.3 (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 postgresql-8.3
dark@Gaia:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree        
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up postgresql-8.3 (8.3.5-0ubuntu8.10) ...
 * Starting PostgreSQL 8.3 database server                                       * Insecure directory in $ENV{PATH} while running with -T switch at /usr/share/postgresql-common/PgCommon.pm line 654.
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.3, action "start" failed.
dpkg: error processing postgresql-8.3 (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 postgresql-8.3
E: Sub-process /usr/bin/dpkg returned an error code (1)
dark@Gaia:~$ sudo apt-get update
Ign http://www.openprinting.org lsb3.2 Release.gpg                             
Ign http://www.openprinting.org lsb3.2/postscript-hp Translation-en_US         
Hit http://us.archive.ubuntu.com intrepid Release.gpg                          
Hit http://security.ubuntu.com intrepid-security Release.gpg                   
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US               
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US        
Get:1 http://www.openprinting.org lsb3.2 Release [26.2kB]                      
Hit http://fr.archive.ubuntu.com hardy Release.gpg                             
Ign http://fr.archive.ubuntu.com hardy/main Translation-en_US                  
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US         
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US           
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US         
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg                  
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US       
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US 
Hit http://us.archive.ubuntu.com intrepid-backports Release.gpg                
Ign http://us.archive.ubuntu.com intrepid-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-backports/main Translation-en_US     
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US  
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US    
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US  
Hit http://security.ubuntu.com intrepid-security Release                       
Ign http://www.openprinting.org lsb3.2/postscript-hp Packages                  
Ign http://us.archive.ubuntu.com intrepid-backports/multiverse Translation-en_US
Hit http://fr.archive.ubuntu.com hardy Release                                 
Hit http://www.openprinting.org lsb3.2/postscript-hp Packages                  
Ign http://us.archive.ubuntu.com intrepid-backports/universe Translation-en_US 
Hit http://security.ubuntu.com intrepid-security/main Packages                 
Hit http://us.archive.ubuntu.com intrepid Release                              
Hit http://us.archive.ubuntu.com intrepid-updates Release                      
Hit http://us.archive.ubuntu.com intrepid-backports Release                    
Hit http://fr.archive.ubuntu.com hardy/main Packages                           
Hit http://security.ubuntu.com intrepid-security/restricted Packages           
Hit http://security.ubuntu.com intrepid-security/main Sources                  
Hit http://security.ubuntu.com intrepid-security/restricted Sources            
Hit http://security.ubuntu.com intrepid-security/universe Packages             
Hit http://us.archive.ubuntu.com intrepid/main Packages                        
Hit http://us.archive.ubuntu.com intrepid/restricted Packages                  
Hit http://us.archive.ubuntu.com intrepid/main Sources                     
Hit http://us.archive.ubuntu.com intrepid/restricted Sources                   
Hit http://security.ubuntu.com intrepid-security/universe Sources              
Hit http://security.ubuntu.com intrepid-security/multiverse Packages       
Hit http://security.ubuntu.com intrepid-security/multiverse Sources        
Hit http://us.archive.ubuntu.com intrepid/universe Packages                
Hit http://us.archive.ubuntu.com intrepid/universe Sources                 
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-updates/main Sources             
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Sources       
Hit http://us.archive.ubuntu.com intrepid-backports/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-backports/main Packages
Hit http://us.archive.ubuntu.com intrepid-backports/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid-backports/universe Packages
Ign http://ppa.launchpad.net intrepid Release.gpg    
Ign http://ppa.launchpad.net intrepid/main Translation-en_US
Ign http://ppa.launchpad.net intrepid Release.gpg
Ign http://ppa.launchpad.net intrepid/main Translation-en_US
Get:2 http://ppa.launchpad.net intrepid Release.gpg [307B]
Ign http://ppa.launchpad.net intrepid/main Translation-en_US
Get:3 http://ppa.launchpad.net intrepid Release [27.6kB]
Get:4 http://ppa.launchpad.net intrepid Release [27.6kB]
Get:5 http://ppa.launchpad.net intrepid Release [27.6kB]
Ign http://ppa.launchpad.net intrepid Release
Ign http://ppa.launchpad.net intrepid/main Packages
Ign http://ppa.launchpad.net intrepid/main Sources
Ign http://ppa.launchpad.net intrepid/main Packages
Ign http://ppa.launchpad.net intrepid/main Packages
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://ppa.launchpad.net intrepid/main Sources                             
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://ppa.launchpad.net intrepid/main Packages                            
Fetched 311B in 7s (43B/s)                                                     
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: You may want to run apt-get update to correct these problems
dark@Gaia:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  consolekit hal-info libck-connector0 libpam-ck-connector libpq-dev libpq5
  libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins
  libxine1-x postgresql-8.3 postgresql-client-8.3
14 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 7968kB of archives.
After this operation, 77.8kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com intrepid-updates/main libpq-dev 8.3.6-0ubuntu8.10 [184kB]
Get:2 http://us.archive.ubuntu.com intrepid-updates/main libpq5 8.3.6-0ubuntu8.10 [290kB]
Get:3 http://us.archive.ubuntu.com intrepid-updates/main postgresql-client-8.3 8.3.6-0ubuntu8.10 [727kB]
Get:4 http://us.archive.ubuntu.com intrepid-updates/main postgresql-8.3 8.3.6-0ubuntu8.10 [3662kB]
Get:5 http://us.archive.ubuntu.com intrepid-updates/main libck-connector0 0.2.10-1ubuntu10 [14.8kB]
Get:6 http://us.archive.ubuntu.com intrepid-updates/main consolekit 0.2.10-1ubuntu10 [93.2kB]
Get:7 http://us.archive.ubuntu.com intrepid-updates/main hal-info 20090128-0ubuntu1~intrepid2 [46.1kB]
Get:8 http://us.archive.ubuntu.com intrepid-updates/main libpam-ck-connector 0.2.10-1ubuntu10 [7966B]
Get:9 http://us.archive.ubuntu.com intrepid-updates/main libxine1 1.1.15-0ubuntu3.1intrepid1 [1318B]
Get:10 http://us.archive.ubuntu.com intrepid-updates/main libxine1-x 1.1.15-0ubuntu3.1intrepid1 [212kB]
Get:11 http://us.archive.ubuntu.com intrepid-updates/main libxine1-ffmpeg 1.1.15-0ubuntu3.1intrepid1 [393kB]
Get:12 http://us.archive.ubuntu.com intrepid-updates/main libxine1-console 1.1.15-0ubuntu3.1intrepid1 [61.4kB]
Get:13 http://us.archive.ubuntu.com intrepid-updates/main libxine1-misc-plugins 1.1.15-0ubuntu3.1intrepid1 [931kB]
Get:14 http://us.archive.ubuntu.com intrepid-updates/main libxine1-bin 1.1.15-0ubuntu3.1intrepid1 [1344kB]
Fetched 7968kB in 6min38s (20.0kB/s)                                           
(Reading database ... 173877 files and directories currently installed.)
Preparing to replace libpq-dev 8.3.5-0ubuntu8.10 (using .../libpq-dev_8.3.6-0ubuntu8.10_i386.deb) ...
Unpacking replacement libpq-dev ...
Preparing to replace libpq5 8.3.5-0ubuntu8.10 (using .../libpq5_8.3.6-0ubuntu8.10_i386.deb) ...
Unpacking replacement libpq5 ...
Preparing to replace postgresql-client-8.3 8.3.5-0ubuntu8.10 (using .../postgresql-client-8.3_8.3.6-0ubuntu8.10_i386.deb) ...
Unpacking replacement postgresql-client-8.3 ...
Preparing to replace postgresql-8.3 8.3.5-0ubuntu8.10 (using .../postgresql-8.3_8.3.6-0ubuntu8.10_i386.deb) ...
 * Stopping PostgreSQL 8.3 database server                                       * Insecure directory in $ENV{PATH} while running with -T switch at /usr/share/postgresql-common/PgCommon.pm line 654.
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.3, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 255
dpkg - trying script from the new package instead ...
 * Stopping PostgreSQL 8.3 database server                                       * Insecure directory in $ENV{PATH} while running with -T switch at /usr/share/postgresql-common/PgCommon.pm line 654.
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.3, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/postgresql-8.3_8.3.6-0ubuntu8.10_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 255
 * Starting PostgreSQL 8.3 database server                                       * Insecure directory in $ENV{PATH} while running with -T switch at /usr/share/postgresql-common/PgCommon.pm line 654.
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.3, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 255
Preparing to replace libck-connector0 0.2.10-1ubuntu9 (using .../libck-connector0_0.2.10-1ubuntu10_i386.deb) ...
Unpacking replacement libck-connector0 ...
Preparing to replace consolekit 0.2.10-1ubuntu9 (using .../consolekit_0.2.10-1ubuntu10_i386.deb) ...
Unpacking replacement consolekit ...
Preparing to replace hal-info 20081124-0ubuntu1~intrepid (using .../hal-info_20090128-0ubuntu1~intrepid2_all.deb) ...
Unpacking replacement hal-info ...
Preparing to replace libpam-ck-connector 0.2.10-1ubuntu9 (using .../libpam-ck-connector_0.2.10-1ubuntu10_i386.deb) ...
Unpacking replacement libpam-ck-connector ...
Preparing to replace libxine1 1.1.15-0ubuntu3.1 (using .../libxine1_1.1.15-0ubuntu3.1intrepid1_i386.deb) ...
Unpacking replacement libxine1 ...
Preparing to replace libxine1-x 1.1.15-0ubuntu3.1 (using .../libxine1-x_1.1.15-0ubuntu3.1intrepid1_i386.deb) ...
Unpacking replacement libxine1-x ...
Preparing to replace libxine1-ffmpeg 1.1.15-0ubuntu3.1 (using .../libxine1-ffmpeg_1.1.15-0ubuntu3.1intrepid1_i386.deb) ...
Unpacking replacement libxine1-ffmpeg ...
Preparing to replace libxine1-console 1.1.15-0ubuntu3.1 (using .../libxine1-console_1.1.15-0ubuntu3.1intrepid1_i386.deb) ...
Unpacking replacement libxine1-console ...
Preparing to replace libxine1-misc-plugins 1.1.15-0ubuntu3.1 (using .../libxine1-misc-plugins_1.1.15-0ubuntu3.1intrepid1_i386.deb) ...
Unpacking replacement libxine1-misc-plugins ...
Preparing to replace libxine1-bin 1.1.15-0ubuntu3.1 (using .../libxine1-bin_1.1.15-0ubuntu3.1intrepid1_i386.deb) ...
Unpacking replacement libxine1-bin ...
Processing triggers for man-db ...
Processing triggers for hal ...
Regenerating hal fdi cache ...
 * Restarting Hardware abstraction layer hald                            [ OK ] 
Errors were encountered while processing:
 /var/cache/apt/archives/postgresql-8.3_8.3.6-0ubuntu8.10_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Thanks!

---

### Post by AllenGG on 2009-02-16
Why not use Synaptic ?  Go to EDIT > Fix broken packages. Then "Reload", then go to updates.

---

### Post by Dark Samurai on 2009-02-16
When I go to reload, it gives me this error:
```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

```

And when I go to "Mark All Upgrades", it gives me this error:
```
E: /var/cache/apt/archives/postgresql-8.3_8.3.6-0ubuntu8.10_i386.deb: subprocess new pre-removal script returned error exit status 255

```

---

### Post by tommcd on 2009-02-17
```
 * Starting PostgreSQL 8.3 database server                                       * Insecure directory in $ENV{PATH} while running with -T switch at /usr/share/postgresql-common/PgCommon.pm line 654.

```

It looks like this is your problem. Try commenting out (place a # in front of) line 654 in /usr/share/postgresql-common/PgCommon.pm.

To do this, open a terminal and run:
```
gksudo gedit /usr/share/postgresql-common/PgCommon.pm
```
and put a # in front of line 654.

I don't have the postgresql directory in /usr/share. Did you install the postgresql package? Perhaps uninstalling it will fix it.

Here is some info about postgresql package:
[https://help.ubuntu.com/community/PostgreSQL](https://help.ubuntu.com/community/PostgreSQL)
[http://www.ubuntugeek.com/howto-setup-database-server-with-postgresql-and-pgadmin3.html](http://www.ubuntugeek.com/howto-setup-database-server-with-postgresql-and-pgadmin3.html)

---

### Post by Dark Samurai on 2009-02-17
Hey-
That partially worked in that it stopped the error, but now there is a new one:
```
dark@Gaia:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up postgresql-8.3 (8.3.6-0ubuntu8.10) ...
 * Starting PostgreSQL 8.3 database server                                       * The PostgreSQL server failed to start. Please check the log output:
2009-02-17 17:48:31 MST FATAL:  could not access private key file "server.key": Permission denied
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.3, action "start" failed.
dpkg: error processing postgresql-8.3 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 postgresql-8.3
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So... What I was thinking of doing was purging postgresql, then reinstall it.  Any input on that?  If I am to purge it, what should be my specific command (what files need to be included)?
Thanks!

---

### Post by tommcd on 2009-02-18
> **Dark Samurai said:**
> 
                                                                        
So... What I was thinking of doing was purging postgresql, then reinstall it.  Any input on that?  If I am to purge it, what should be my specific command (what files need to be included)?
Thanks!

Postgresql is an optional package. I do not have it on my system.
[http://packages.ubuntu.com/intrepid/postgresql](http://packages.ubuntu.com/intrepid/postgresql)
Did you install this? Do you need it? 
To purge it run this from terminal:
```
sudo apt-get remove --purge postgresql
```
If you don't need it then don't reinstall it.

---

### Post by Dark Samurai on 2009-02-18
Thank you very very *very* much!  I purged it from my system and now it all works fine!
Thanks again!

---

### Post by kambalipattu on 2011-07-31
Errors were encountered while processing:
 gforge-db-postgresql
 gforge-web-apache2
 gforge-plugin-globalsearch
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

