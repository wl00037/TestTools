

	（1）当前分支的代码再测试环境触发的SQL，会调用DBA接口，DBA接口会查询七天内是否有相同SQL的慢查询记录；
	（2）如果DBA记录中没有这个记录，会有Mysql的explain命令；
	（3）如果没有利用到索引，并且扫描后得出影响行数过多，也会进行阻断；

就是把分支部署时期，所有的SQL都记录下来，逐条去查线上，是否出现了慢查询（7天内），如果没出现则不阻塞，不关注SQL是否和本次分支有关，先上出现则强制阻断