# MBook
总结性文档


线程安全日期处理：
public class DateUtil {
    private static ThreadLocal<DateFormat> sdfThreadLocal = new ThreadLocal<DateFormat>() {
        @Override
        public SimpleDateFormat initialValue() {
            return new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        }
    };

    public static String formatDate(Date date) throws ParseException {
        return sdfThreadLocal.get().format(date);
    }

    public static Date parse(String strDate) throws ParseException {

        return sdfThreadLocal.get().parse(strDate);
    }

}

