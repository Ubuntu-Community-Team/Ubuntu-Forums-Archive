---
title: "Upgrading eclipse PDT"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by Findarato on 2009-08-28
Hello everyone,

When I try to update Eclipse, with the PDT Framework installed, I get a dependency error. Instead of bothering people to see how I could solve that, I was wondering if I can simply download the newer version from eclipse.org and replace the old one ? Will my workspace settings still be in place ?

Thank you very much for your help,

Findarato

---

### Post by Findarato on 2009-08-28
Could anyone please help me out here ?

These are the errors I am getting while upgrading :
Cannot complete the request.  See the details.
Unsatisfied dependency: [org.eclipse.php.feature.group 2.1.1.v20090708-1127-7L7979F8NcJKhKOR99SkWJ] requiredCapability: org.eclipse.equinox.p2.iu/org.eclipse.wst.web_ui.feature.feature.group/[3.1.0,4.0.0)
Unsatisfied dependency: [org.eclipse.php.feature.group 2.1.1.v20090708-1127-7L7979F8NcJKhKOR99SkWJ] requiredCapability: org.eclipse.equinox.p2.iu/org.eclipse.wst.common.fproj.feature.group/[3.1.0,4.0.0)
Unsatisfied dependency: [org.eclipse.php.feature.group 2.1.1.v20090708-1127-7L7979F8NcJKhKOR99SkWJ] requiredCapability: org.eclipse.equinox.p2.iu/org.eclipse.wst.jsdt.feature.feature.group/[1.1.0,2.0.0)
Unsatisfied dependency: [org.eclipse.php.feature.group 2.1.1.v20090708-1127-7L7979F8NcJKhKOR99SkWJ] requiredCapability: org.eclipse.equinox.p2.iu/org.eclipse.wst.xsl.feature.feature.group/[1.0.0,2.0.0)
Unsatisfied dependency: [org.eclipse.php.feature.group 2.1.1.v20090708-1127-7L7979F8NcJKhKOR99SkWJ] requiredCapability: org.eclipse.equinox.p2.iu/org.eclipse.wst.xml_ui.feature.feature.group/[3.1.0,4.0.0)
Unsatisfied dependency: [org.eclipse.php.core 2.1.1.v20090721-1634] requiredCapability: osgi.bundle/com.ibm.icu/4.0.1
Unsatisfied dependency: [org.eclipse.php.debug.core 2.1.1.v20090727-0731] requiredCapability: osgi.bundle/com.ibm.icu/4.0.1
Unsatisfied dependency: [org.eclipse.php.debug.ui 2.1.1.v20090714-1338] requiredCapability: osgi.bundle/com.ibm.icu/4.0.1
Unsatisfied dependency: [org.eclipse.php.ui 2.1.1.v20090721-1634] requiredCapability: osgi.bundle/org.eclipse.wst.jsdt.ui/1.0.200
Unsatisfied dependency: [org.eclipse.php.server.ui 2.1.1.v20090707-1108] requiredCapability: osgi.bundle/org.eclipse.help/3.4.0
Unsatisfied dependency: [org.eclipse.php.debug.core 2.1.1.v20090727-0731] requiredCapability: osgi.bundle/com.ibm.icu/4.0.1
Unsatisfied dependency: [org.eclipse.php.core 2.1.1.v20090721-1634] requiredCapability: osgi.bundle/com.ibm.icu/4.0.1
Unsatisfied dependency: [org.eclipse.php.debug.ui 2.1.1.v20090714-1338] requiredCapability: osgi.bundle/com.ibm.icu/4.0.1
Cannot find a solution where both "bundle com.ibm.icu 4.0.1" and "bundle com.ibm.icu [3.8.1,4.0.0)" are satisfied.
Cannot find a solution where both "bundle com.ibm.icu 4.0.1" and "bundle com.ibm.icu [3.8.1.1,4.0.0)" are satisfied.
Cannot find a solution where both "bundle com.ibm.icu 4.0.1" and "bundle com.ibm.icu [3.8.1.1,4.0.0)" are satisfied.
Unsatisfied dependency: [org.eclipse.wst.jsdt.web.ui 1.0.104.v200901282355] requiredCapability: osgi.bundle/org.eclipse.wst.jsdt.ui/[1.0.0,2.0.0)
Unsatisfied dependency: [org.eclipse.php.debug.core 2.1.1.v20090727-0731] requiredCapability: osgi.bundle/com.ibm.icu/4.0.1
Unsatisfied dependency: [org.eclipse.php.server.ui 2.1.1.v20090707-1108] requiredCapability: osgi.bundle/org.eclipse.help/3.4.0
Unsatisfied dependency: [org.eclipse.php.feature.group 2.1.1.v20090708-1127-7L7979F8NcJKhKOR99SkWJ] requiredCapability: org.eclipse.equinox.p2.iu/org.eclipse.php.debug.ui/[2.1.1.v20090714-1338,2.1.1.v20090714-1338]
Unsatisfied dependency: [org.eclipse.php.feature.group 2.1.1.v20090708-1127-7L7979F8NcJKhKOR99SkWJ] requiredCapability: org.eclipse.equinox.p2.iu/org.eclipse.wst.xsl.feature.feature.group/[1.0.0,2.0.0)
Unsatisfied dependency: [org.eclipse.php.feature.group 2.1.1.v20090708-1127-7L7979F8NcJKhKOR99SkWJ] requiredCapability: org.eclipse.equinox.p2.iu/org.eclipse.wst.web_ui.feature.feature.group/[3.1.0,4.0.0)
Unsatisfied dependency: [org.eclipse.php.feature.group 2.1.1.v20090708-1127-7L7979F8NcJKhKOR99SkWJ] requiredCapability: org.eclipse.equinox.p2.iu/org.eclipse.php.server.ui/[2.1.1.v20090707-1108,2.1.1.v20090707-1108]
Unsatisfied dependency: [org.eclipse.php.feature.group 2.1.1.v20090708-1127-7L7979F8NcJKhKOR99SkWJ] requiredCapability: org.eclipse.equinox.p2.iu/org.eclipse.wst.xml_ui.feature.feature.group/[3.1.0,4.0.0)
Unsatisfied dependency: [org.eclipse.php.feature.group 2.1.1.v20090708-1127-7L7979F8NcJKhKOR99SkWJ] requiredCapability: org.eclipse.equinox.p2.iu/org.eclipse.wst.jsdt.feature.feature.group/[1.1.0,2.0.0)
Unsatisfied dependency: [org.eclipse.php.feature.group 2.1.1.v20090708-1127-7L7979F8NcJKhKOR99SkWJ] requiredCapability: org.eclipse.equinox.p2.iu/org.eclipse.wst.common.fproj.feature.group/[3.1.0,4.0.0)
Unsatisfied dependency: [org.eclipse.php.feature.group 2.1.1.v20090708-1127-7L7979F8NcJKhKOR99SkWJ] requiredCapability: org.eclipse.equinox.p2.iu/org.eclipse.php.core/[2.1.1.v20090721-1634,2.1.1.v20090721-1634]
Unsatisfied dependency: [org.eclipse.php.feature.group 2.1.1.v20090708-1127-7L7979F8NcJKhKOR99SkWJ] requiredCapability: org.eclipse.equinox.p2.iu/org.eclipse.php.ui/[2.1.1.v20090721-1634,2.1.1.v20090721-1634]
Unsatisfied dependency: [org.eclipse.php.feature.group 2.1.1.v20090708-1127-7L7979F8NcJKhKOR99SkWJ] requiredCapability: org.eclipse.equinox.p2.iu/org.eclipse.php.debug.core/[2.1.1.v20090727-0731,2.1.1.v20090727-0731]
Unsatisfied dependency: [org.eclipse.php.core 2.1.1.v20090721-1634] requiredCapability: osgi.bundle/com.ibm.icu/4.0.1
Unsatisfied dependency: [org.eclipse.php.ui 2.1.1.v20090721-1634] requiredCapability: osgi.bundle/org.eclipse.wst.jsdt.ui/1.0.200
Unsatisfied dependency: [org.eclipse.php.ui 2.1.1.v20090721-1634] requiredCapability: osgi.bundle/org.eclipse.wst.jsdt.web.ui/0.0.0
Unsatisfied dependency: [org.eclipse.php.ui 2.1.1.v20090721-1634] requiredCapability: java.package/org.eclipse.php.internal.ui.preferences/0.0.0
Unsatisfied dependency: [org.eclipse.php.ui 2.0.0.v20090315-1850] requiredCapability: osgi.bundle/org.eclipse.wst.jsdt.web.ui/1.0.0
Unsatisfied dependency: [org.eclipse.php.ui 2.0.0.v20090315-1850] requiredCapability: java.package/org.eclipse.php.internal.ui.preferences/0.0.0
Unsatisfied dependency: [org.eclipse.php.debug.ui 2.1.1.v20090714-1338] requiredCapability: osgi.bundle/com.ibm.icu/4.0.1
Unsatisfied dependency: [org.eclipse.php.sdk.feature.group 2.1.1.v20090707-1108-51184QACJCPBYeNOmUQaXJduha9O] requiredCapability: org.eclipse.equinox.p2.iu/org.eclipse.php.feature.group/[2.1.1.v20090708-1127-7L7979F8NcJKhKOR99SkWJ,2.1.1.v20090708-1127-7L7979F8NcJKhKOR99SkWJ]

---

### Post by Findarato on 2009-08-28
It worked just replacing it :)

---

