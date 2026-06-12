---
title: "Hardy: Tomcat 5.5 problems..."
date: 2008-08-24
forum: General Help
---

### Post by slusig on 2008-08-24
I have Tomcat 5.5 working on Hardy, but there are a couple things I am having a problem with...

1) I can't find the System.out and System.err output from java.  I have a catalina.out file in /var/log/tomcat5.5, but it only shows startup information.  System.out and System.err messages seem to be directed to another file (or, maybe not captured at all).  I suspect that because tomcat is running as a daemon (/etc/init.d/tomcat5.5), this output is going to another file.  The logging.properties and catalina.properties in $CATALINA_HOME/conf haven't been modified... they are the same as what comes with the Tomcat installation.

2) I've packaged a webapp into a war file.  It has a context.xml file in META-INF.  When I deploy the war file to tomcat, the context.xml correctly goes to $CATALINA_HOME/Catalina/localhost.  But when I try to use the webapp, I get the error message " [FONT="Courier New"]Cannot create JDBC driver of class '' for connect URL 'null'[/FONT] " whenever I try to connect to the database.  If manually configure the context.xml in $CATALINA_HOME/Catalina/localhost to point to my development directory (so that the JSP is compiled at run-time), it works.

Would really appreciate it if someone could help me with this.  Thanks.

---

### Post by hardcrash2 on 2008-10-01
Having the same problem listed in item 1. Any ideas?

---

