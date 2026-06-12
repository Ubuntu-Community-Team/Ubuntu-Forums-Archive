---
title: "Issue in JBoss 5.0.1.GA"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by bharani.82 on 2009-05-20
Hi All,
 
I m getting one strange problem while upgrading from JB0ss4.0.1GA to 5.0.1GA. The EAR file I m using is getting deployed successfully in JBoss4.0.1. But when I m trying to deploy the same EAR in JBoss5.0.1, I m getting the following error.
 
In the ejb-jar.xml I m using I have the following lines of code. I think the lines marked in red colour only giving problem. Can anybody tell what I have to do to successfully deploy this in JBoss5.0.1GA as well. Thanks in Advance, Bharanidharan
 
[SIZE=2][COLOR=#008080]<?[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]xml [/COLOR][/SIZE][SIZE=2][COLOR=#7f007f]version[/COLOR][/SIZE][SIZE=2]=[/SIZE][SIZE=2][COLOR=#2a00ff]"1.0" [/COLOR][/SIZE][SIZE=2][COLOR=#7f007f]encoding[/COLOR][/SIZE][SIZE=2]=[/SIZE][SIZE=2][COLOR=#2a00ff]"UTF-8"[/COLOR][/SIZE][SIZE=2][COLOR=#008080]?>[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]<![/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]DOCTYPE [/COLOR][/SIZE][SIZE=2][COLOR=#000080]ejb-jar [/COLOR][/SIZE]
[SIZE=2][COLOR=#808080]PUBLIC [/COLOR][/SIZE][SIZE=2][COLOR=#000080]"-//Sun Microsystems, Inc.//DTD Enterprise JavaBeans 2.0//EN" [/COLOR][/SIZE]
[SIZE=2][COLOR=#3f7f5f]"http://java.sun.com/dtd/ejb-jar_2_0.dtd"[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]<[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]ejb-jar [/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]<[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]enterprise-beans[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]
[SIZE=2][COLOR=#3f5fbf]<!-- Session Beans -->[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]<[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]session [/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]<[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]description[/COLOR][/SIZE][SIZE=2][COLOR=#008080]><![CDATA[[/COLOR][/SIZE][SIZE=2]Sofa Adaptor EJB[/SIZE][SIZE=2][COLOR=#008080]]]></[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]description[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]<[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]display-name[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE][SIZE=2]Sofa Adaptor EJB[/SIZE][SIZE=2][COLOR=#008080]</[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]display-name[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]<[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]ejb-name[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE][SIZE=2]SofaAdaptor[/SIZE][SIZE=2][COLOR=#008080]</[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]ejb-name[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]
[COLOR=red][SIZE=2]<[/SIZE][SIZE=2]service-endpoint[/SIZE][SIZE=2]>[/SIZE][SIZE=2]com.hp.bpo.adaptor.webservice.SofaAdaptorEndpoint[/SIZE][SIZE=2]</[/SIZE][SIZE=2]service-endpoint[/SIZE][SIZE=2]>[/SIZE][/COLOR]
[SIZE=2][COLOR=#008080]<[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]home[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE][SIZE=2]com.hp.bpo.adaptor.ejb.interfaces.SofaAdaptorServicesHome[/SIZE][SIZE=2][COLOR=#008080]</[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]home[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]<[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]remote[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE][SIZE=2]com.hp.bpo.adaptor.ejb.interfaces.SofaAdaptorServices[/SIZE][SIZE=2][COLOR=#008080]</[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]remote[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]<[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]ejb-class[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE][SIZE=2]com.hp.bpo.adaptor.ejb.SofaAdaptorServicesBean[/SIZE][SIZE=2][COLOR=#008080]</[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]ejb-class[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]<[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]session-type[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE][SIZE=2]Stateless[/SIZE][SIZE=2][COLOR=#008080]</[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]session-type[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]<[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]transaction-type[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE][SIZE=2]Container[/SIZE][SIZE=2][COLOR=#008080]</[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]transaction-type[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]<[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]ejb-ref[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]<[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]ejb-ref-name[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE][SIZE=2]ejb/Employee[/SIZE][SIZE=2][COLOR=#008080]</[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]ejb-ref-name[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]<[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]ejb-ref-type[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE][SIZE=2]Session[/SIZE][SIZE=2][COLOR=#008080]</[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]ejb-ref-type[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]<[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]home[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE][SIZE=2]com.hp.bpo.xdal.employee.ejb.interfaces.EmployeeDataAccessHome[/SIZE][SIZE=2][COLOR=#008080]</[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]home[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]<[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]remote[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE][SIZE=2]com.hp.bpo.xdal.employee.ejb.interfaces.EmployeeDataAccess[/SIZE][SIZE=2][COLOR=#008080]</[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]remote[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]</[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]ejb-ref[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]<[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]resource-ref[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]<[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]res-ref-name[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE][SIZE=2]oracleDS[/SIZE][SIZE=2][COLOR=#008080]</[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]res-ref-name[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]<[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]res-type[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE][SIZE=2]java.sql.DataSource[/SIZE][SIZE=2][COLOR=#008080]</[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]res-type[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]<[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]res-auth[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE][SIZE=2]Container[/SIZE][SIZE=2][COLOR=#008080]</[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]res-auth[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]</[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]resource-ref[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]</[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]session[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]</[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]enterprise-beans[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]
[SIZE=2][COLOR=#008080]</[/COLOR][/SIZE][SIZE=2][COLOR=#3f7f7f]ejb-jar[/COLOR][/SIZE][SIZE=2][COLOR=#008080]>[/COLOR][/SIZE]

 
A part of error message is,
 
org.jboss.deployers.spi.DeploymentException: Error creating managed object for v
fszip:/C:/jboss-5.0.1.GA/server/Sample/deploy/SOFA/SOFA.ear/SOFAAdaptor.jar/
at org.jboss.deployers.spi.DeploymentException.rethrowAsDeploymentExcept
ion(DeploymentException.java:49)
at org.jboss.deployers.spi.deployer.helpers.AbstractParsingDeployerWithO
utput.createMetaData(AbstractParsingDeployerWithOutput.java:337)
at org.jboss.deployers.spi.deployer.helpers.AbstractParsingDeployerWithO
utput.createMetaData(AbstractParsingDeployerWithOutput.java:297)
at org.jboss.deployers.spi.deployer.helpers.AbstractParsingDeployerWithO
utput.createMetaData(AbstractParsingDeployerWithOutput.java:269)
 
Caused by: org.jboss.xb.binding.JBossXBException: Failed to parse source: Elemen
t type "service-endpoint" must be declared. @ vfszip:/C:/jboss-5.0.1.GA/server/S
ample/deploy/SOFA/SOFA.ear/SOFAAdaptor.jar/META-INF/ejb-jar.xml[80,28]
at org.jboss.xb.binding.parser.sax.SaxJBossXBParser.parse(SaxJBossXBPars
er.java:203)
at org.jboss.xb.binding.UnmarshallerImpl.unmarshal(UnmarshallerImpl.java
:168)
at org.jboss.deployers.vfs.spi.deployer.JBossXBDeployerHelper.parse(JBos
sXBDeployerHelper.java:199)
at org.jboss.deployers.vfs.spi.deployer.JBossXBDeployerHelper.parse(JBos
sXBDeployerHelper.java:170)
at org.jboss.deployers.vfs.spi.deployer.SchemaResolverDeployer.parse(Sch
emaResolverDeployer.java:132)
 
Caused by: org.xml.sax.SAXException: Element type "service-endpoint" must be dec
lared. @ vfszip:/C:/jboss-5.0.1.GA/server/Sample/deploy/SOFA/SOFA.ear/SOFAAdapto
r.jar/META-INF/ejb-jar.xml[80,28]
at org.jboss.xb.binding.parser.sax.SaxJBossXBParser$MetaDataErrorHandler
.error(SaxJBossXBParser.java:426)
at org.apache.xerces.util.ErrorHandlerWrapper.error(Unknown Source)
at org.apache.xerces.impl.XMLErrorReporter.reportError(Unknown Source)
at org.apache.xerces.impl.XMLErrorReporter.reportError(Unknown Source)
at org.apache.xerces.impl.XMLErrorReporter.reportError(Unknown Source)
at org.apache.xerces.impl.dtd.XMLDTDValidator.handleStartElement(Unknown
 
 
Thanks,
Bharanidharan

---

