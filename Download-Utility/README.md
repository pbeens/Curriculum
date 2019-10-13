# README.md

To make downloading of all the resources easier I found this [Linux script](https://www.linuxjournal.com/content/downloading-entire-web-site-wget) which can be modified (the last line) to download an entire site.

In the comments of that site there was a recommendation to add the line `--random-wait` in case the server watches for a utility like this and shuts it down, which I have added.

Just replace the last line of the script with the URL you want to download. Note that this runs on Linux. 

The final script looks like this:

```sh
wget \
     --recursive \
     --random-wait \
     --no-clobber \
     --page-requisites \
     --html-extension \
     --convert-links \
     --restrict-file-names=windows \
     --domains www.edu.gov.mb.ca \
     --no-parent \
         https://www.edu.gov.mb.ca/k12/cur/index.html
```

Another option that works is:

 ```sh
$ wget -e robots=off -r -np 'http://example.com/folder/'

* -e robots=off causes it to ignore robots.txt for that domain
* -r makes it recursive
* -np = no parents, so it doesn't follow links up to the parent folder
```