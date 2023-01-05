### PolyGlit

This is a fork of git that I use for polyglot file purposes. It allows creating git bundles of a repository where specific files are not compressed.

#### Installation Instructions (Ubuntu)

- Clone this repo
- `sudo apt install libssl-dev libcurl4-openssl-dev gettext`
- `make && make install`

Now you have a special build of `git` in `~/bin`

#### Usage

Run this in any git repository

```
~/bin/git bundle create output.file --do-not-compress `git hash-object uncompressed.file` --all
```

#### Example

```
mkdir test && cd test
echo "This will be in plaintext in the bundle" > clear.txt
echo "This will be encrypted" > encrypted.txt
git init && git add . && git commit -m "test"
~/bin/git bundle create bundle.file --do-not-compress `git hash-object clear.txt` --all
```

If you open `bundle.file` you will find the plaintext
