# 附录B 并发库的简单比较

虽然，C++11才开始正式支持并发，不过，高级编程语言都支持并发和多线程已经不是什么新鲜事了。例如，Java在第一个发布版本中就支持多线程编程，在某些平台上也提供符合POSIX C标准的多线程接口，还有[Erlang](http://www.erlang.org/)支持消息的同步传递(有点类似于MPI)。当然还有使用C++类的库，比如Boost，其将底层多线程接口进行包装，适用于任何给定的平台(不论是使用POSIX C的接口，或其他接口)，其对支持的平台会提供可移植接口。

这些库或者编程语言，已经写了很多多线程应用，并且在使用这些库写多线程代码的经验，可以借鉴到C++中，本附录就对Java，POSIX C，使用Boost线程库的C++，以及C++11中的多线程工具进行简单的比较，当然也会交叉引用本书的相关章节。

<table border=1>
  <td> 特性 </td>
  <td> 启动线程 </td>
  <td> 互斥量 </td>
  <td> 监视/等待谓词 </td>
  <td> 原子操作和并发感知内存模型 </td>
  <td> 线程安全容器 </td>
  <td> Futures(期望) </td>
  <td> 线程池 </td>
  <td> 线程中断 </td>
<tr>
  <td>章节引用</td>
  <td>第2章</td>
  <td>第3章</td>
  <td>第4章</td>
  <td>第5章</td>
  <td>第6章和第7章</td>
  <td>第4章</td>
  <td>第9章</td>
  <td>第9章</td>
</tr>
<tr>
  <td rowspan=3> C++11 </td>
  <td rowspan=3> std::thread和其成员函数 </td>
  <td> std::mutex类和其成员函数 </td>
  <td> std::condition_variable </td>
  <td> std::atomic_xxx类型 </td>
  <td rowspan=3> N/A </td>
  <td> std::future<> </td>
  <td rowspan=3> N/A </td>
  <td rowspan=3> N/A </td>
</tr>
<tr>
  <td> std::lock_guard<>模板 </td>
  <td rowspan=2> std::condition_variable_any类和其成员函数 </td>
  <td> std::atomic<>类模板 </td>
  <td> std::shared_future<> </td>
</tr>
<tr>
  <td> std::unique_lock<>模板 </td>
  <td> std::atomic_thread_fence()函数 </td>
  <td> std::atomic_future<>类模板 </td>
</tr>
<tr>
  <td rowspan=3> Boost线程库 </td>
  <td rowspan=3> boost::thread类和成员函数 </td>
  <td> boost::mutex类和其成员函数 </td>
  <td> boost::condition_variable类和其成员函数 </td>
  <td rowspan=3> N/A </td>
  <td rowspan=3> N/A </td>
  <td> boost::unique_future<>类模板</td>
  <td rowspan=3> N/A </td>
  <td rowspan=3> boost::thread类的interrupt()成员函数</td>
</tr>
<tr>
  <td> boost::lock_guard<>类模板 </td>
  <td rowspan=2> boost::condition_variable_any类和其成员函数 </td>
  <td rowspan=2> boost::shared_future<>类模板</td>
</tr>
<tr>
  <td> boost::unique_lock<>类模板 </td>
</tr>
<tr>
  <td rowspan=4> POSIX C </td>
  <td> pthread_t类型相关的API函数 </td>
  <td> pthread_mutex_t类型相关的API函数</td>
  <td> pthread_cond_t类型相关的API函数</td>
  <td rowspan=4> N/A </td>
  <td rowspan=4> N/A </td>
  <td rowspan=4> N/A </td>
  <td rowspan=4> N/A </td>
  <td rowspan=4> pthread_cancel() </td>
</tr>
<tr>
  <td> pthread_create() </td>
  <td> pthread_mutex_lock() </td>
  <td> pthread_cond_wait() </td>
</tr>
<tr>
  <td> pthread_detach() </td>
  <td> pthread_mutex_unlock() </td>
  <td> pthread_cond_timed_wait() </td>
</tr>
<tr>
  <td> pthread_join() </td>
  <td> 等等 </td>
  <td> 等等 </td>
</tr>
<tr>
  <td> Java </td>
  <td> java.lang.thread类 </td>
  <td> synchronized块 </td>
  <td> java.lang.Object类的wait()和notify()函数，用在内部synchronized块中 </td>
  <td> java.util.concurrent.atomic包中的volatile类型变量 </td>
  <td> java.util.concurrent包中的容器 </td>
  <td> 与java.util.concurrent.future接口相关的类 </td>
  <td> java.util.concurrent.ThreadPoolExecutor类 </td>
  <td> java.lang.Thread类的interrupt()函数 </td>
</tr>
</table>