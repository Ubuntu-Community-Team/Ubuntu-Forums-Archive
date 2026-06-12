---
title: "karmic: opensync barry plugin not working?"
date: 2009-12-23
forum: Hardware
---

### Post by IndieRockSteve on 2009-12-23
$ apt-show-versions -a|grep opensync-plugin-barry
opensync-plugin-barry 0.14-2.1ubuntu1 install ok installed
opensync-plugin-barry 0.14-2.1ubuntu1 karmic us.archive.ubuntu.com
opensync-plugin-barry/karmic uptodate 0.14-2.1ubuntu1
opensync-plugin-barry-dbg 0.14-2.1ubuntu1 install ok installed
opensync-plugin-barry-dbg 0.14-2.1ubuntu1 karmic us.archive.ubuntu.com
opensync-plugin-barry-dbg/karmic uptodate 0.14-2.1ubuntu1 

$ msynctool --addmember blackberry barry-sync
Unable to instance plugin with name barry-sync: Unable to find the plugin "barry-sync"

anyone know why this isn't working?

---

