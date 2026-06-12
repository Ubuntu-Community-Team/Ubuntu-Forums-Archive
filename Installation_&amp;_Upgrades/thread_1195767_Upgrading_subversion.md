---
title: "Upgrading subversion"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by mgazb on 2009-06-24
Hi,

I have been caught out by tools upgrading their version of subversion. I have several PCs on a closed network running Ubuntu 7.0.4. Cygwin on Windows PCs has moved on to 1.5.x and 1.6.x as has Tortoise.

Can any one tell me whether I can use binaries built for later versions? 

Is there a required upgrade path for this?

thanks

---

### Post by andreseso on 2009-06-24
Several years ago I switched my subversion repository from subversion on one machine to another machine running ubuntu.  Basically the steps are to export the existing repository to a plain binary backup, set up the new repository on the new machine and import the backup file

> svnadmin help dump
dump: usage: svnadmin dump REPOS_PATH [-r LOWER[:UPPER]] [--incremental]

Dump the contents of filesystem to stdout in a 'dumpfile'
portable format, sending feedback to stderr.  Dump revisions
LOWER rev through UPPER rev.  If no revisions are given, dump all
revision trees.  If only LOWER is given, dump that one revision tree.
If --incremental is passed, then the first revision dumped will be
a diff against the previous revision, instead of the usual fulltext.

Valid options:
  -r [--revision] ARG      : specify revision number ARG (or X:Y range)
  --incremental            : dump incrementally
  --deltas                 : use deltas in dump output
  -q [--quiet]             : no progress (only errors) to stderr

svnadmin help load
load: usage: svnadmin load REPOS_PATH

Read a 'dumpfile'-formatted stream from stdin, committing
new revisions into the repository's filesystem.  If the repository
was previously empty, its UUID will, by default, be changed to the
one specified in the stream.  Progress feedback is sent to stdout.

Valid options:
  -q [--quiet]             : no progress (only errors) to stderr
  --ignore-uuid            : ignore any repos UUID found in the stream
  --force-uuid             : set repos UUID to that found in stream, if any
  --use-pre-commit-hook    : call pre-commit hook before committing revisions
  --use-post-commit-hook   : call post-commit hook after committing revisions
  --parent-dir ARG         : load at specified directory in repository


The reference manual is the official subversion manual which should be easy to google for.
I believe the necesary steps are:

[LIST=1]
[*]Set up an subversion repository on the new server with apache hooks and all the rest
[*]End any relationship between production and subversion

[*]Have all developers commit their changes to subversion even if they do not work.  
[*]Tell the developers to take a well earned break.
[*]Make backup on old server subversion file system with svnadmin dump
[*]Move backup to new server
[*]Load backup in new repository with svnadmin load
[*]Have all developers make backup of their working copies
[*]Have all developers check out a new working copy from the new subversion server
[*]Fix any bugs introduced by committing incomplete files.

[/LIST]

One detail to take into consideration is that revisions larger than 2GB will break some subversion servers.  I had that happen to me on edgy or feisty. Ubuntu upgraded the subversion software to a version that did not have the 2GB revision limit.

Love,
Andres

---

