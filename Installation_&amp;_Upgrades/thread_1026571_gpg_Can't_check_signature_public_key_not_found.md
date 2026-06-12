---
title: "gpg: Can't check signature: public key not found"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by sprucio on 2008-12-31
I just tried downloading the squid source files and this error was generated: ```
gpg: Can't check signature: public key not found

```Can anyone tell me what steps I need to take to fix this?

---

### Post by lemming465 on 2009-01-01
More details would help.  Where were you downloading the source from, is there a reason you aren't using the Ubuntu squid source package, and how much do you know about gnupg and the PGP web of trust?

The short answer is that the squid project signs their source releases with a PGP signature.  To verify the signature you have to first import the corresponding public key into a gnupg keyring. You can get the public key from either 
wget [http://www.squid-cache.org/pgp.asc](http://www.squid-cache.org/pgp.asc) followed by gpg --import, or from gpg --recv-keys --keyserver subkeys.pgp.net FF5CF463

Figuring out whether or not you trust the key to actually be from the squid project is an entirely separate issue.

---

### Post by sprucio on 2009-01-02
The error is generated when I run "apt-get source." The repository is from Ubuntu although I'm not sure which repository it comes from.

I'm not sure how Ubuntu package system works so I assumed that it had already imported the public keys from the repositories in /etc/apt/sources.list. Do I need to import the public keys manually?

---

### Post by lemming465 on 2009-01-02
I'm not an expert on Ubuntu packaging, but what I think is going on is:

**binaries** - synaptic and apt-get import keys from /usr/share/keyrings/ into a gpg keyring /etc/apt/trusted.gpg.  This is done automatically for the 2 main Ubuntu keys, and by hand for 3rd party repositories (typically in the synapic "repositories" or "software sources" dialog on the "authentication" tab).  You can see what's in there at the command line by doing something like *gpg --keyring /etc/apt/trusted.gpg --fingerprint*.  See "man apt-secure" for more details.

It's not actually verifying signatures on the .deb package files themselves, but rather on the release files for the archive the package comes from.  The integrity of the signature on the release file lets apt or aptitude or synaptic trust the md5 checksum of the package from the release file, and that *is* validated against a fresh checksum of the package before installing it. You are trusting the repository maintainer not to ship bad stuff, and to protect the private half of his or her signing key.

**source** packages actually use a dpkg-sig signature on the package itself, but in this case the signing key is from the maintainer who uploaded it to the source repository, and the keyring is your gnupg default keyring.  If you don't go around collecting all the public keys of all the debian and ubuntu maintainers, then that key isn't on your keyring, and you get the warning message.  However, /etc/dpkg/dpkg.cfg on ubuntu specifies *no-debsig*, which means by default this is only a warning and not a fatal error.  

Bottom line: "apt-get source" will often complain about inability to to verify a signature, but it will run dpkg-deb --extract for you anyway in spite of that.

If you are feeling highly paranoid, you track down the public key of the package maintainer, check to see if it is in your web of trust, and verify the signature.  If you are feeling only moderately paranoid, you are very paranoid about which source repositories you trust, and you wait at least a week before installing a package, and then you google it to see if anyone has complained about corrupted archives or other problems before you install it.  If you have very low security paranoia, you just blithely build and install it without checking any further.

---

