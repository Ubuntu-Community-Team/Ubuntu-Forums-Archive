---
title: "HOWTO: Copy queue management with Krusader 2.0.0-beta2 compiled on Intrepid"
date: 2008-11-30
forum: General Help
---

### Post by rebegin on 2008-11-30
Hello all,
I hope i opened the thread into it's right place. if no than please let me know where it should be.

generally the new version (2.0.0-beta2) what's from svn brings the long awaited "F5-F2 magic" into Krusader but there's some work with it to get it compiled on Intrepid:

get the source:
```
sudo apt-get install subversion
```
```
svn co http://krusader.svn.sourceforge.net/svnroot/krusader/trunk/krusader_kde4
```

enter to the created directory:
```
cd krusader_kde4
```

*[edit]*: if you want to update the source next time just run this in the "krusader_kde4" directory:
```
svn up
```

some quick editing...
this idea is coming from conradmr ( [http://ubuntuforums.org/showpost.php?p=6272957&postcount=2](http://ubuntuforums.org/showpost.php?p=6272957&postcount=2) )
> However due to an incorrect dependency in the cmake files from the kdelibs5 package, the build fails:

make[2]: *** No rule to make target `/build/buildd/kde4libs-4.1.2/obj-i486-linux-gnu/lib/libkdecore.so', needed by `lib/libkopete.so.4.1.0'. Stop.

It looks like this dependency is caused by the following lines in /usr/share/kde4/apps/cmake/modules/KDELibsDependenciesInternal.cmake:

SET("solid_LIB_DEPENDS" "general;/usr/lib/libQtCore.so;general;/usr/lib/libQtDBus.so;general;/usr/lib/libQtXml.so;general;/usr/lib/libQtGui.so;general;/build/buildd/kde4libs-4.1.2/obj-i486-linux-gnu/lib/libkdecore.so;")

SET("solid_LIB_DEPENDS" "/usr/lib/libQtCore.so;/usr/lib/libQtDBus.so;/usr/lib/libQtXml.so;/usr/lib/libQtGui.so;/build/buildd/kde4libs-4.1.2/obj-i486-linux-gnu/lib/libkdecore.so;")

The reference to the /build/buildd path looks like a left-over from the package build system. These paths should instead reference /usr/lib.

Changing these paths to /usr/lib/libkdecore.so fixes the problem for me.

so in my case as i use xubuntu (if you use ubuntu just replace mousepad with gedit ):
```
gksudo mousepad /usr/share/kde4/apps/cmake/modules/KDELibsDependenciesInternal.cmake
```

and do the replacements mentioned abowe.
after this:

```
cmake -DCMAKE_INSTALL_PREFIX=/usr/ -DQT_INCLUDES=/usr/share/qt4/include
```

if it doesn't work just install the dependencies mentioned in the INSTALL file, this one for example:
```
sudo apt-get install kdelibs5-dev
```

```
make
```

installing 
- *[update]* checkinstall has created a package for me and it successfully installed through the package manager so it's easier to update and also to get rid of it... you can download mine for Intrepid 64bit from here:
[krusader_2.0~svn6170-1ubuntu1-1_amd64.deb]("http://viridis.hu/~rebegin/xubuntu/krusader_2.0~svn6170-1ubuntu1-1_amd64.deb")
by the way creating and installing your own package using checkinstall is as easy as:
```
sudo checkinstall
```
it might be better to change the name from krusader-kde4 to krusader and the version to "2.0~svn6170-1ubuntu1" and simply change the value "svn6170" to the one you get after getting the code through subversion...


- [previously] i didn't install it as it's possible to run the Krusader executable from the "krusader" folder so i just modified my launcher icon...but should work something like this:
```
su -c "make install"
```

sorry for my english...

enjoy

---

