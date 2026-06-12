---
title: "SVN: I messed up..."
date: 2008-08-02
forum: General Help
---

### Post by ccw127 on 2008-08-02
I was using svn, internet died part way through. I deleted directory. Now svn says:

chris@chris-laptop:~/Desktop/eAthena$ svn co [http://svn.eathena.ws/svn/ea/branches/stable/](http://svn.eathena.ws/svn/ea/branches/stable/) .
svn: '.' is already a working copy for a different URL; run 'svn update' to complete it

chris@chris-laptop:~/Desktop/eAthena$ svn update
svn: Working copy '.' locked
svn: run 'svn cleanup' to remove locks (type 'svn help cleanup' for details)

chris@chris-laptop:~/Desktop/eAthena$ svn cleanup
svn: In directory '.'
svn: Error processing command 'modify-wcprop' in '.'
svn: 'mapserv-sql.bat' is not under version control

chris@chris-laptop:~/Desktop/eAthena$ 

when I try to use svn to start over... Help????

Chris

---

