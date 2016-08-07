# A package manager for the web

Bower is a tool that helps you manager your 3rd client side libraries (packages) in your web project.
(like as Bootstrap, JQuery, Angular...)

Normally if you need use a library, you will: Browse => Find Link => Download => Extract => Find => Copy => Add to html file.

But with Bower: Bower Install Package =>  Use

**Features**
1. Save time (tell Bower package you want, Bower will download and stick them right in your project)
2. Package up to date.
3. Create your own package and share.


**Outlines content**

1. Basics (install/uninstall packages)
2. Config (keep track installed pack)
3. Advanced
4. Publishing (your own pack for others to consume)

--

**1. Basic**

	1. Setup Bower
		- Install Nodejs (NPM included with Node)
		- npm install bower -g
		- If you use Windows, you need install Git for Windows
	2. Install/Uninstall
		- bower install lodash
		- bower uninstall lodash (delete directory in bower_components folder)
	3. Specific version
		- bower install lodash#2.2.1
		- bower info lodash (find version list)
	4. Updating Packages
		- bower update (update all packages to latest version)
		- bower install lodash (upate a pack)
	5. Listing packages
		- bower list (check available packages in project)
	6. Searching
		- bower search package-name
		- Or search at bower.io/search (keyword search)

**2. Config**

	1. Create a bower.json file
		- bower init
	2. .bowerrc - customize the install directory for our packages. (in your own directory)
		- Create new file .bowerrc 
			{
				"directory": "js/lib"
			}
		- Move all packages from bower_components to js/lib
		- Note: From now, if you install a new package, it will be installed to js/lib, but not add pack in bower.json (see #4) (so, you should creat .bowerrc at the beginning)
	3. Install from bower.json
		- bower install (The same npm install)
	4. Adding & Removing packages and keeping our bower.json up to date.
		- bower install lodash --save (or --save-dev)
		- bower uninstall lodash --save

**3. Advanced**

	1. Cache
		- bower cache list
		- bower cache clean
		- bower install lodash -o (force Bower to go into offline mode)
	2. Install options
		- bower install ../BowerFundamentalFiles (install the files from that repo into local project)
		- bower install http://code.jquery,com/jquery-2.11.0.js (install just that file to lib)
		- bower install --production (not install devDependencies packages).
		- bower install _lo=lodash (install package lodash with your favourite name directory, here is _lo)
	3. Help
		- bower help
		- bower help install
	4. Info
		- bower info lodash
	5. Lookup
		- bower lookup angular (display the url of angular package)
	6. Prune
		- bower prune (uninstall any dependencies you've got that aren't indicated in the bower.json, extraneous package)
	7. Best practices:
		- Create .bowerrc.
		- Create bower.json (without bower init)
			{
				"name": "bower-tutorial"
			}
		- Install packages: bower install bootstrap lodash angular --save
		- If you want to contain packages that relate to test follow this:
			- Create test folder and lib as sub-directory
			- Create another .bowerrc in new lib 
				{
					"directory": "lib"
				}
			- Create another bower.json in new lib
				{
					"name": "bower-tutorial-test"
				}
			- Change your command-line to test folder and run bower install --save-dev jasmine
		
**4. Publishing a Bower package**

	1. Create & Publish the package
		- bower init 
		- Create actual app file (app.js)
		- Add package to Github
			- Create repo and push to Github.
			- Because Bower works off a tags. Each tag is a release for Bower. So we need tag your project: git tag 0.0.1 (version num in bower.json)
			- git push --tags
		- Register with Bower
			- bower register pack-name git://github.com/username/pack-name.git
	2. Create new version
		- Edit code & Update git repo.
		- Change version in bower.json to 0.0.2 for example.
		- git tag 0.0.2
		- git push --tags
	3. Update the Package
		- bower update