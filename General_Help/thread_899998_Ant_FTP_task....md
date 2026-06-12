---
title: "Ant FTP task..."
date: 2008-08-24
forum: General Help
---

### Post by slusig on 2008-08-24
I have a target setup in Ant to FTP files but it isn't working.  I get this error:
```
 Could not create type ftp due to java.lang.NoClassDefFoundError: org/apache/commons/net/ftp/FTPClientConfig
```  

ant-commons-net.jar is in /usr/share/ant/lib, but it doesn't seem to pick it up automatically.  I also tried setting up an environment variable ANT_HOME pointing to /usr/share/ant.  

Any ideas?

Here is what my build.xml file looks like:
```
<target name="ftp" description="FTP static content to web server">
    <ftp server="servername" port="21" remotedir="/www/html" userid="username" password="password" depends="yes" binary="no">
      <fileset dir="${dist.home}/static">
         <exclude name="**/*.jsp" />
      </fileset>
    </ftp>
  </target>
```

---

### Post by twschmidt on 2009-03-18
After searching around I found that /usr/share/java/commons-net.jar was not symbolically linked in my /usr/share/ant/lib directory.  To see if this fixes the problem do:
```

ant -lib /usr/share/java/commons-net.jar
```


If that does remove your error then create a symlink
```

cd /usr/share/ant/lib
sudo ln -s /usr/share/java/commons-net.jar .
```

---

### Post by paradroid on 2010-04-15
if commons-net.jar doesn't exist:

```
apt-get install libcommons-net-java

```

---

