##Bug description
If I run: 

	    python manage.py test

I get the following correct output:
```bash
		(pycharm_repro)rburhum@peru.local ~/src/pycharm_repro/pycharm_repro $ python manage.py test
		nosetests --verbosity 1
		Creating test database for alias 'default'...
		..
		----------------------------------------------------------------------
		Ran 2 tests in 0.001s

		OK
		Destroying test database for alias 'default'...
		(pycharm_repro)
```

However, in pycharm, instead of running `python manage.py test`, it is executing `nosetests --verbosity 1 test`
which causes the GUI to run a whole bunch of tests for a long time and keeps spitting errors like this:

```bash
		/Users/rburhum/.virtualenvs/pycharm_repro/bin/python "/Applications/PyCharm 2.7 EAP.app/helpers/pycharm/django_test_manage.py" test test /Users/rburhum/src/pycharm_repro/pycharm_repro
		Testing started at 9:32 AM ...
		nosetests --verbosity 1 test
		test test_builtin failed -- Traceback (most recent call last):
		  File "/usr/local/Cellar/python/2.7.2/Frameworks/Python.framework/Versions/2.7/lib/python2.7/test/test_builtin.py", line 469, in test_execfile
		    execfile(TESTFN, globals)
		IOError: [Errno 2] No such file or directory: '@test_14695_tmp'

		Skipping test_concat because of memory constraint
		Skipping test_optimized_concat because of memory constraint
		test test_cmath failed -- Traceback (most recent call last):
		  File "/usr/local/Cellar/python/2.7.2/Frameworks/Python.framework/Versions/2.7/lib/python2.7/test/test_cmath.py", line 352, in test_specific_values
		    msg=error_message)
		  File "/usr/local/Cellar/python/2.7.2/Frameworks/Python.framework/Versions/2.7/lib/python2.7/test/test_cmath.py", line 94, in rAssertAlmostEqual
		    'got {!r}'.format(a, b))
		AssertionError: atan0000: atan(complex(0.0, 0.0))
		Expected: complex(0.0, 0.0)
		Received: complex(0.0, -0.0)
		Received value insufficiently close to expected value.

		test test_cpickle failed -- multiple errors occurred
		test test_ctypes failed -- multiple errors occurred
		test test_descr failed -- Traceback (most recent call last):
		  File "/usr/local/Cellar/python/2.7.2/Frameworks/Python.framework/Versions/2.7/lib/python2.7/test/test_descr.py", line 1947, in test_recursions_1
		    self.fail("expected a RuntimeError for print recursion")
		AssertionError: expected a RuntimeError for print recursion

		test test_distutils failed -- Traceback (most recent call last):
		  File "/usr/local/Cellar/python/2.7.2/Frameworks/Python.framework/Versions/2.7/lib/python2.7/distutils/tests/test_sysconfig.py", line 39, in test_get_python_lib
		    self.assertEqual(_sysconfig.get_path('platstdlib'), res)
		AssertionError: '/Users/rburhum/.virtualenvs/pycharm_repro/lib/python2.7' != '/usr/local/Cellar/python/2.7.2/Frameworks/Python.framework/Versions/2.7/lib/python2.7'

		test test_email failed -- multiple errors occurred
		test test_email_renamed failed -- multiple errors occurred
```


### To reproduce

	- Clone the repo
	- mkvirtualenv pycharm_repro
	- pip install -r requirements.txt`
	- python manage.py test
	- Setup the same thing in Pycharm
