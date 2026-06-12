---
title: "Funambol Works. Reboot, Funambol Fails"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by sickanimations on 2009-02-10
After much work and configuration I got Funambol Server running on my machine and I got my Pocket PC and two Thunderbird / Lightning clients connected and Synced. All was good and well.

I copy the funambol-server script to /etc/init.d and then do update-rc.d and reboot.

That's funny, none of the devices will connect. I manually run the server with /opt/Funambol/bin/funambol-server

No problems here...

There's a Java GUI Admin that comes with it so I tried connecting ... "not found"

Jump in firefox, go to localhost:8080/funambol/ds and there's a page full of exceptions (read below) :(

However I can view localhost:8080/funambol but it's not the useful part - just a basic interface.

So I backed up Funambol, deleted (including conf) and reinstalled from the .bin. 

Same problem :( Why? Why when it worked so well and did exactly what I wanted it to do, did it start failing? Did I do something?

All I've been doing is messing around with deluge and Ktorrent... They wouldn't have interfered, would they?

Won't you pleeeeeeeeeee-eaaaaaaaase help me :guitar:

Cheers.

The Error:
```

HTTP Status 500 -

type Exception report

message

description The server encountered an internal error () that prevented it from fulfilling this request.

exception

javax.servlet.ServletException: Error bootstrapping Sync4jServlet
	com.funambol.transport.http.server.Sync4jServlet.bootstrap(Sync4jServlet.java:687)
	com.funambol.transport.http.server.Sync4jServlet.init(Sync4jServlet.java:220)
	javax.servlet.GenericServlet.init(GenericServlet.java:212)
	org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:102)
	org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:286)
	org.apache.coyote.http11.Http11Processor.process(Http11Processor.java:844)
	org.apache.coyote.http11.Http11Protocol$Http11ConnectionHandler.process(Http11Protocol.java:583)
	org.apache.tomcat.util.net.JIoEndpoint$Worker.run(JIoEndpoint.java:447)
	java.lang.Thread.run(Thread.java:595)

root cause

com.funambol.framework.config.ConfigurationException: Error creating the Officer object
	com.funambol.server.config.Configuration.getOfficer(Configuration.java:383)
	com.funambol.transport.http.server.Sync4jServlet.bootstrap(Sync4jServlet.java:641)
	com.funambol.transport.http.server.Sync4jServlet.init(Sync4jServlet.java:220)
	javax.servlet.GenericServlet.init(GenericServlet.java:212)
	org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:102)
	org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:286)
	org.apache.coyote.http11.Http11Processor.process(Http11Processor.java:844)
	org.apache.coyote.http11.Http11Protocol$Http11ConnectionHandler.process(Http11Protocol.java:583)
	org.apache.tomcat.util.net.JIoEndpoint$Worker.run(JIoEndpoint.java:447)
	java.lang.Thread.run(Thread.java:595)

root cause

com.funambol.framework.config.ConfigurationException: Error in creating an instance of com/funambol/server/security/UserProvisioningOfficer.xml
	com.funambol.server.config.ConfigCache.getBeanInstance(ConfigCache.java:175)
	com.funambol.server.config.ConfigTools.getBeanInstance(ConfigTools.java:92)
	com.funambol.server.config.Configuration.getOfficer(Configuration.java:376)
	com.funambol.transport.http.server.Sync4jServlet.bootstrap(Sync4jServlet.java:641)
	com.funambol.transport.http.server.Sync4jServlet.init(Sync4jServlet.java:220)
	javax.servlet.GenericServlet.init(GenericServlet.java:212)
	org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:102)
	org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:286)
	org.apache.coyote.http11.Http11Processor.process(Http11Processor.java:844)
	org.apache.coyote.http11.Http11Protocol$Http11ConnectionHandler.process(Http11Protocol.java:583)
	org.apache.tomcat.util.net.JIoEndpoint$Worker.run(JIoEndpoint.java:447)
	java.lang.Thread.run(Thread.java:595)

root cause

com.funambol.framework.config.ConfigurationException: Error creating the UserManager object
	com.funambol.server.config.Configuration.getUserManager(Configuration.java:435)
	com.funambol.server.security.DBOfficer.init(DBOfficer.java:86)
	com.funambol.server.security.UserProvisioningOfficer.init(UserProvisioningOfficer.java:69)
	com.funambol.framework.tools.beans.BeanFactory.getBeanInstanceFromConfig(BeanFactory.java:269)
	com.funambol.server.config.ConfigCache.getBeanInstance(ConfigCache.java:168)
	com.funambol.server.config.ConfigTools.getBeanInstance(ConfigTools.java:92)
	com.funambol.server.config.Configuration.getOfficer(Configuration.java:376)
	com.funambol.transport.http.server.Sync4jServlet.bootstrap(Sync4jServlet.java:641)
	com.funambol.transport.http.server.Sync4jServlet.init(Sync4jServlet.java:220)
	javax.servlet.GenericServlet.init(GenericServlet.java:212)
	org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:102)
	org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:286)
	org.apache.coyote.http11.Http11Processor.process(Http11Processor.java:844)
	org.apache.coyote.http11.Http11Protocol$Http11ConnectionHandler.process(Http11Protocol.java:583)
	org.apache.tomcat.util.net.JIoEndpoint$Worker.run(JIoEndpoint.java:447)
	java.lang.Thread.run(Thread.java:595)

root cause

com.funambol.framework.config.ConfigurationException: Error in creating an instance of com/funambol/server/admin/DBUserManager.xml
	com.funambol.server.config.ConfigCache.getNewBeanInstance(ConfigCache.java:126)
	com.funambol.server.config.ConfigTools.getNewBeanInstance(ConfigTools.java:74)
	com.funambol.server.config.Configuration.getUserManager(Configuration.java:428)
	com.funambol.server.security.DBOfficer.init(DBOfficer.java:86)
	com.funambol.server.security.UserProvisioningOfficer.init(UserProvisioningOfficer.java:69)
	com.funambol.framework.tools.beans.BeanFactory.getBeanInstanceFromConfig(BeanFactory.java:269)
	com.funambol.server.config.ConfigCache.getBeanInstance(ConfigCache.java:168)
	com.funambol.server.config.ConfigTools.getBeanInstance(ConfigTools.java:92)
	com.funambol.server.config.Configuration.getOfficer(Configuration.java:376)
	com.funambol.transport.http.server.Sync4jServlet.bootstrap(Sync4jServlet.java:641)
	com.funambol.transport.http.server.Sync4jServlet.init(Sync4jServlet.java:220)
	javax.servlet.GenericServlet.init(GenericServlet.java:212)
	org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:102)
	org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:286)
	org.apache.coyote.http11.Http11Processor.process(Http11Processor.java:844)
	org.apache.coyote.http11.Http11Protocol$Http11ConnectionHandler.process(Http11Protocol.java:583)
	org.apache.tomcat.util.net.JIoEndpoint$Worker.run(JIoEndpoint.java:447)
	java.lang.Thread.run(Thread.java:595)

root cause

com.funambol.framework.tools.beans.BeanInitializationException: Error getting connection in SQLHelperClause initialization
	com.funambol.server.admin.DBUserManager.init(DBUserManager.java:190)
	com.funambol.framework.tools.beans.BeanFactory.getBeanInstanceFromConfig(BeanFactory.java:269)
	com.funambol.server.config.ConfigCache.getNewBeanInstance(ConfigCache.java:124)
	com.funambol.server.config.ConfigTools.getNewBeanInstance(ConfigTools.java:74)
	com.funambol.server.config.Configuration.getUserManager(Configuration.java:428)
	com.funambol.server.security.DBOfficer.init(DBOfficer.java:86)
	com.funambol.server.security.UserProvisioningOfficer.init(UserProvisioningOfficer.java:69)
	com.funambol.framework.tools.beans.BeanFactory.getBeanInstanceFromConfig(BeanFactory.java:269)
	com.funambol.server.config.ConfigCache.getBeanInstance(ConfigCache.java:168)
	com.funambol.server.config.ConfigTools.getBeanInstance(ConfigTools.java:92)
	com.funambol.server.config.Configuration.getOfficer(Configuration.java:376)
	com.funambol.transport.http.server.Sync4jServlet.bootstrap(Sync4jServlet.java:641)
	com.funambol.transport.http.server.Sync4jServlet.init(Sync4jServlet.java:220)
	javax.servlet.GenericServlet.init(GenericServlet.java:212)
	org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:102)
	org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:286)
	org.apache.coyote.http11.Http11Processor.process(Http11Processor.java:844)
	org.apache.coyote.http11.Http11Protocol$Http11ConnectionHandler.process(Http11Protocol.java:583)
	org.apache.tomcat.util.net.JIoEndpoint$Worker.run(JIoEndpoint.java:447)
	java.lang.Thread.run(Thread.java:595)

root cause

org.apache.tomcat.dbcp.dbcp.SQLNestedException: Cannot create PoolableConnectionFactory (socket creation error)
	org.apache.tomcat.dbcp.dbcp.BasicDataSource.createDataSource(BasicDataSource.java:1225)
	org.apache.tomcat.dbcp.dbcp.BasicDataSource.getConnection(BasicDataSource.java:880)
	com.funambol.server.admin.DBUserManager.init(DBUserManager.java:187)
	com.funambol.framework.tools.beans.BeanFactory.getBeanInstanceFromConfig(BeanFactory.java:269)
	com.funambol.server.config.ConfigCache.getNewBeanInstance(ConfigCache.java:124)
	com.funambol.server.config.ConfigTools.getNewBeanInstance(ConfigTools.java:74)
	com.funambol.server.config.Configuration.getUserManager(Configuration.java:428)
	com.funambol.server.security.DBOfficer.init(DBOfficer.java:86)
	com.funambol.server.security.UserProvisioningOfficer.init(UserProvisioningOfficer.java:69)
	com.funambol.framework.tools.beans.BeanFactory.getBeanInstanceFromConfig(BeanFactory.java:269)
	com.funambol.server.config.ConfigCache.getBeanInstance(ConfigCache.java:168)
	com.funambol.server.config.ConfigTools.getBeanInstance(ConfigTools.java:92)
	com.funambol.server.config.Configuration.getOfficer(Configuration.java:376)
	com.funambol.transport.http.server.Sync4jServlet.bootstrap(Sync4jServlet.java:641)
	com.funambol.transport.http.server.Sync4jServlet.init(Sync4jServlet.java:220)
	javax.servlet.GenericServlet.init(GenericServlet.java:212)
	org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:102)
	org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:286)
	org.apache.coyote.http11.Http11Processor.process(Http11Processor.java:844)
	org.apache.coyote.http11.Http11Protocol$Http11ConnectionHandler.process(Http11Protocol.java:583)
	org.apache.tomcat.util.net.JIoEndpoint$Worker.run(JIoEndpoint.java:447)
	java.lang.Thread.run(Thread.java:595)

root cause

java.sql.SQLException: socket creation error
	org.hsqldb.jdbc.Util.sqlException(Unknown Source)
	org.hsqldb.jdbc.jdbcConnection.<init>(Unknown Source)
	org.hsqldb.jdbcDriver.getConnection(Unknown Source)
	org.hsqldb.jdbcDriver.connect(Unknown Source)
	org.apache.tomcat.dbcp.dbcp.DriverConnectionFactory.createConnection(DriverConnectionFactory.java:38)
	org.apache.tomcat.dbcp.dbcp.PoolableConnectionFactory.makeObject(PoolableConnectionFactory.java:294)
	org.apache.tomcat.dbcp.dbcp.BasicDataSource.validateConnectionFactory(BasicDataSource.java:1247)
	org.apache.tomcat.dbcp.dbcp.BasicDataSource.createDataSource(BasicDataSource.java:1221)
	org.apache.tomcat.dbcp.dbcp.BasicDataSource.getConnection(BasicDataSource.java:880)
	com.funambol.server.admin.DBUserManager.init(DBUserManager.java:187)
	com.funambol.framework.tools.beans.BeanFactory.getBeanInstanceFromConfig(BeanFactory.java:269)
	com.funambol.server.config.ConfigCache.getNewBeanInstance(ConfigCache.java:124)
	com.funambol.server.config.ConfigTools.getNewBeanInstance(ConfigTools.java:74)
	com.funambol.server.config.Configuration.getUserManager(Configuration.java:428)
	com.funambol.server.security.DBOfficer.init(DBOfficer.java:86)
	com.funambol.server.security.UserProvisioningOfficer.init(UserProvisioningOfficer.java:69)
	com.funambol.framework.tools.beans.BeanFactory.getBeanInstanceFromConfig(BeanFactory.java:269)
	com.funambol.server.config.ConfigCache.getBeanInstance(ConfigCache.java:168)
	com.funambol.server.config.ConfigTools.getBeanInstance(ConfigTools.java:92)
	com.funambol.server.config.Configuration.getOfficer(Configuration.java:376)
	com.funambol.transport.http.server.Sync4jServlet.bootstrap(Sync4jServlet.java:641)
	com.funambol.transport.http.server.Sync4jServlet.init(Sync4jServlet.java:220)
	javax.servlet.GenericServlet.init(GenericServlet.java:212)
	org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:102)
	org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:286)
	org.apache.coyote.http11.Http11Processor.process(Http11Processor.java:844)
	org.apache.coyote.http11.Http11Protocol$Http11ConnectionHandler.process(Http11Protocol.java:583)
	org.apache.tomcat.util.net.JIoEndpoint$Worker.run(JIoEndpoint.java:447)
	java.lang.Thread.run(Thread.java:595)

```

---

### Post by sickanimations on 2009-02-12
Well I got it up and running again but I really don't want to risk restoring configuration .xmls so I've started from scratch.

Here's what I did:
rm -r /opt/Funambol
rm -r /bin/funambol
I wasn't doing the bin funambol before, but I wouldn't have thought there were any conf files in there.

The error was Tomcat / JDBC related as far as I could tell from log output on ALL but to tell the truth I really couldn't afford to spend much time fixing it.

Semi solved?

---

### Post by technomensch on 2009-03-09
Which version of Ubuntu are you using?  I just upgraded to Jaunty Server Alpha 5 with LAMP and Tomcat.

I don't suppose you'd be willing to post a step-by-step guide, including any issues you came across/how you resolved them?

If you do, I'm on the docs team and would love to put it in the wiki.  I'm sure I'm not the only one interested.

---

### Post by technomensch on 2009-03-10
Never mind.  I'm not done, but at least I've got my web client demo working using the following:

[https://wiki.ubuntu.com/marckaplan/funambol](https://wiki.ubuntu.com/marckaplan/funambol)

This is a template for a full blown article I'll be moving into the wiki when I've got it fully working.

---

