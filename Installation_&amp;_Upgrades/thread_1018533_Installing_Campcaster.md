---
title: "Installing Campcaster"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by themagicmanfromtrent on 2008-12-22
I'm relatively new to ubuntu, and was wondering how i could possibly install software on here. I've been having problems with Synaptics, but I think it's ok for now.

There's a software called campcaster which I want to try out, so I went to the site and clicked download on [this]("http://www.campware.org/en/camp/campcaster_news/") page, and I got to [this]("http://sourceforge.net/project/showfiles.php?group_id=136949") page. Now I didn't know which one to choose, as I have no clue what dapper is. I clicked on the first one, and I get a campcaster archive and a campacter_libraries archive. I'm not sure which one to download, so I download the first one.

Once I've downloaded and extracted the top one, i get a folder. I click on the install notes, and it says to look in doc/installubuntu.html. I read this page, and it says the following:

> Installation instructions
1. Install the tools, libraries and services
Run the apt-get install command given on our wiki page.
2. Obtain the Campcaster sources
If you are reading this, you probably already have the sources, so you can skip to the next step.

If you do not have the sources yet, you need to get the tarballs named campcaster-<version>.tar.bz2 and campcaster-libraries-<version>.tar.bz2. Both can be downloaded from [http://sourceforge.net/projects/campcaster/](http://sourceforge.net/projects/campcaster/).
3. Compile and install Campcaster
To install Campcaster in /opt/campcaster, do the following:

tar xfj campcaster-<version>.tar.bz2
tar xfj campcaster-libraries-<version>.tar.bz2
cd campcaster-<version>
./configure --prefix=/opt/campcaster --with-apache-group=www-data
sudo make install

4. Configure the external services
Before you can use Campcaster, you need to set up and configure the web server and the database that Campcaster uses to store its data. Type the following:

sudo ./bin/postInstallStation.sh --directory=/opt/campcaster \
                --apache-group=www-data \
                --postgresql-dir=/etc/postgresql/8.1/main \
                --postgresql-init-script=/etc/init.d/postgresql-8.1

5. Start Campcaster
After a successful installation, the Campcaster scheduler has to be started, by typing:

/opt/campcaster/bin/campcaster-scheduler.sh start

To use the the web interface, point your browser to [http://localhost/campcaster](http://localhost/campcaster). You can also use the web interface from other computers; simply put the name or IP number of the computer where Campcaster was installed in place of localhost.

To start Campcaster Studio, type the following:

/opt/campcaster/bin/campcaster-studio.sh

For your first login, use the following values:

    * username: root
    * password: q

Later you can change the password, and add more users, from the web interface.

You can make the scheduler start automatically when the system boots up, by doing the following:

sudo cp /opt/livesupport/etc/campcaster-scheduler /etc/init.d/
sudo update-rc.d campcaster-scheduler defaults 92

You can quickly fill your Campcaster storage with audio files using the mass import script:

sudo /opt/campcaster/bin/import.sh --directory=<some directory>

Have fun! 

To start with the apt-get thing is linked to [this]("http://code.campware.org/projects/campcaster/wiki/DevelopmentEnvironment#a1.Installpackages") page. Now I am completely and utterly confused as to which directions to follow.

There's also a config file in the directory. Should I run that??

1. Which campcaster files should I download?

2. Where do I start??

3. What's dapper?

4. Do I run the config file?

Easy questions, I know...

---

### Post by DieB on 2008-12-22
well dapper is the 6.06 version of ubuntu. As for both have the same version numbers, i would choose the dapper link, download all three packages and afterwards doubleclik it, gdebi should start and give u the opportuinity to install. (it might be the best way to install the library package first.)

hope it is a solution.

---

### Post by DieB on 2008-12-22
for installation issues and so forth this might be wort a look:

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by themagicmanfromtrent on 2009-01-20
Ah, turns out campcaster ain't compatible with Ibex.

No wonder.

They just released a beta version which only works on hardy. Looks like i'll have to wait.

Thanks.

---

### Post by kamarysan on 2009-03-19
i try to instal on ubuntu 8.10 and all was a failure.  hoepe somebady will help me

---

### Post by themagicmanfromtrent on 2009-03-19
Don't bother. Use Gutsy or Hardy for Campcaster 1.3 or use Hardy for 1.4

---

### Post by toneranger on 2009-05-10
Hi, i'm a newbie trying to install campcaster on a fresh install of ubuntu 8.04 hardy heron.
 
No joy at all as i cannot get pass the install of libs. Error dependency messages unixodbc and then libid3tag using latest beta of campcaster (1.4) with 1.3 error is libid3tag
 
Any ideas ?

---

### Post by Partyboi2 on 2009-05-10
> **toneranger said:**
> Hi, i'm a newbie trying to install campcaster on a fresh install of ubuntu 8.04 hardy heron.
 
No joy at all as i cannot get pass the install of libs. Error dependency messages unixodbc and then libid3tag using latest beta of campcaster (1.4) with 1.3 error is libid3tag
 
Any ideas ?
f you are installing a deb package and have dependency errors you will need to install the missing packages so try installing
unixodbc and libid3tag0
```
sudo apt-get install unixodbc libid3tag0 
```

---

### Post by toneranger on 2009-05-10
Thanks for that. Just tried installing unixodbc and get package unixodbc is not available, but is referred by another package, this may mean that the package is missing, has been obseleted, or is only available from another source
E:package unixodbc has no installation candidate.
 
Same with libid3tag0
 
Kind Regards toneranger

---

### Post by Partyboi2 on 2009-05-10
Can you open a terminal and post the output to
```
sudo apt-get update
```

---

### Post by Randem on 2009-08-18
Any success anyone?  I am in the process of installing Campcaster on Jaunty and am getting cppunit errors during *make install*.

Cheers.

---

### Post by Partyboi2 on 2009-08-19
Have you got the libcppunit-dev package installed?
[B]
[/B]

---

### Post by Randem on 2009-08-19
Thanks Partyboi2,

Yes, the libcppunit-1.12-1 is installed.
I have included more details regarding the errors in [COLOR=Blue][another thread]("http://ubuntuforums.org/showthread.php?t=1243266")[/COLOR].

Cheers

---

